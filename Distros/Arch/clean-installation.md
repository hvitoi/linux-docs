# Arch installation

```sh
# Connect to Wi-Fi
wifi-menu

# Mirror list
nano /etc/pacman.d/mirrorlist

# Format partitions
cfdisk
mkfs.fat -F32 /dev/sda1
mkfs.ext4 /dev/sda2

# Mount root partition
mount /dev/sda2 /mnt

# Baixa pacotes
pacstrap /mnt base base-devel linux linux-firmware

# Create fstab
genfstab -U /mnt >> /mnt/etc/fstab

# Change root directory
arch-chroot /mnt

# Install grub
pacman -S grub efibootmgr
mkdir /efi
mount /dev/sda1 /efi
grub-install --target=x86_64-efi --efi-directory=/efi --bootloader-id=GRUB
grub-mkconfig -o /boot/grub/grub.cfg

# Install gnome
pacman -S gnome

# Habilitate services
systemctl enable gdm.service
systemctl enable NetworkManager.service
system ctl enable bluetooth.services

# Configure localization settings
pacman -S nano
nano /etc/locale.gen
locale-gen
```

# Arch installation

- Installation image: <https://archlinux.org/download/>

```sh
# Connect to Wi-Fi
iwctl
[iwd] device list
[iwd] station `device` get-networks
[iwd] station `device` connect `ssid`
ping archlinux.org

# Update system clock
timedatectl set-ntp true

# Partitions
lsblk
fdisk -l # List disks
mkfs.ext4 /dev/sdx1
mkswap /dev/sdx2

# Mount root partition
mount /dev/sdx1 /mnt
swapon /dev/sdx2
df -h # Show mounted partitions

# Select mirrors
vi /etc/pacman.d/mirrorlist
pacman -Syy # Test mirrors

# Install system
pacstrap /mnt base base-devel linux-lts linux-firmware vim

# Generate fstab
genfstab -U /mnt >> /mnt/etc/fstab

# Chroot
arch-chroot /mnt

# Language and region
ln -sf /usr/share/zoneinfo/Region/City /etc/localtime
hwclock --systohc
locale-gen  # Edit /etc/locale.gen first
# Create /etc/locale.conf with LANG=en_US.UTF-8

# Hostname and hosts
/etc/hostname
#yourhostname
/etc/hosts
#127.0.0.1 localhost
#::1 localhost

# Root password
passwd

# Install additional packages
pacman -S intel-ucode bluez bluez-utils mesa nvidia nvidia-utils gnome zsh

# Install grub
pacman -S grub efibootmgr os-prober
mkdir /efi
mount /dev/sdx1 /efi
grub-install --target=x86_64-efi --efi-directory=/efi --bootloader-id=GRUB
grub-mkconfig -o /boot/grub/grub.cfg

# Create user
useradd -m -d /home/hvitoi -s /bin/zsh hvitoi
usermod -aG wheel hvitoi
passwd hvitoi

# Configure sudo for the user
EDITOR=vim visudo # Uncomment %wheel ALL=(ALL) ALL

# Enable services
systemctl enable gdm.service
systemctl enable NetworkManager.service
systemctl enable bluetooth.service

# Reboot (first exit chroot)
reboot
```

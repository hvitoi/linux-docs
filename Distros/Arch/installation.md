# Arch installation

- Installation image: <https://archlinux.org/download/>

```sh
# Connect to Wi-Fi
iwctl
[iwd] device list
[iwd] station `device` scan
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
pacman -Syyy # Test mirrors

# Install system
pacstrap /mnt base base-devel linux linux-firmware

# Generate fstab
genfstab -U /mnt >> /mnt/etc/fstab

# Chroot
arch-chroot /mnt

# Language and region
ln -sf /usr/share/zoneinfo/Region/City /etc/localtime
hwclock --systohc
locale-gen  # Edit /etc/locale.gen
# Create /etc/locale.conf with LANG=en_US.UTF-8

# Hostname and hosts
/etc/hostname
/etc/hosts

# Root password
passwd

# Initial ramdisk for the linux kernel
mkinitcpio -p linux

# Install grub
pacman -S grub efibootmgr os-prober
mkdir /efi
mount /dev/sdx1 /efi
grub-install --target=x86_64-efi --efi-directory=/efi --bootloader-id=GRUB
grub-mkconfig -o /boot/grub/grub.cfg

# Reboot
sudo reboot
```

```sh

# Create user
useradd -m -G wheel hvitoi
passwd hvitoi

# Configure sudo for the user
EDIT=vim visudo # Uncomment %wheel ALL=(ALL) ALL

# Other packages
pacman -S intel-ucode
pacman -S xorg-server
pacman -S mesa # intel graphics
pacman -S nvidia nvidia-utils
pacman -S virtualbox-guest-utils xf86-video-vmware # only for VM

# Update system clock
timedatectl set-ntp true
timedatectl status
```

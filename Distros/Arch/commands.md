# Commands

```sh
ip link
ip addr show / ip a
wifi-menu
ping google.com
dhcpcd

# Update system clock

timedatectl set-ntp true
timedatectl status

# Mirror list

nano /etc/pacman.d/mirrorlist

# Test mirrors

pacman -Syyy

# Create tables and partition

fdisk -l
lsblk
fdisk /dev/sdc
g - create gpt partition table
p - print the partition table
n - new partition
t - partition type
w - write changes

# Format partitions

mkfs.fat -F32 /dev/sdc1
mkfs.ext4 /dev/sdc2

# Mount partitions

mount /dev/sdc2 /mnt
mount
df -h # Show mounted partitions

# Make swap file

fallocate -l 4G /swapfile
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile
echo '/swapfile none swap sw 0 0' | tee -a /etc/fstab # Append new swap item to fstab (only if created after the genfstab command)

# Make swap partitio

mkswap /dev/sdb1 # Define particao (ou arquivo) sdb1 como swap
swapon /dev/sdb1 # Ativa o swap
swapon --show
echo '/swapfile none swap sw 0 0' | tee -a /etc/fstab # Append new swap item to fstab (only if created after the genfstab command)

# Baixa pacotes

pacstrap /mnt base linux linux-firmware

# fstab says where partitions should be mounted

genfstab -U /mnt >> /mnt/etc/fstab
cat /mnt/etc/fstab

# Change to the machine installation

arch-chroot /mnt

# Install packages

pacman -S nano
pacman -S networkmanager wpa_supplicant wireless_tools netctl
pacman -S dialog
pacman -S sudo

# Enable autostart

systemctl enable NetworkManager

# Initial ramdisk for the linux kernel

mkinitcpio -p linux

# Password for the root user

passwd

# Create user

useradd -m -g users -G wheel Henrique
passwd Henrique

# Configure sudo for the user

EDIT=nano visudo # Uncomment %wheel ALL=(ALL) ALL

# Instalar grub

pacman -S grub efibootmgr os-prober # dosfstools mtools
mkdir /boot/efi
mount /dev/sdc1 /boot/efi
grub-install --target=x86_64-efi --bootloader-id=grub_uefi --recheck
mkdir /boot/grub/locale
cp /usr/share/locale/en\@quot/LC_MESSAGES/grub.mo /boot/grub/locale/en.mo
grub-mkconfig -o /boot/grub/grub.cfg

# Other packages

pacman -S intel-ucode
pacman -S xorg-server
pacman -S mesa # intel graphics
pacman -S nvidia nvidia-utils
pacman -S virtualbox-guest-utils xf86-video-vmware # only for VM

# Finalizing

exit
poweroff
reboot

# Install gnome

pacman -Syyy
pacman -S gnome
systemctl enable gdm
pacman -Syu
reboot
```

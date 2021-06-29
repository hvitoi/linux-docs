# Arch installation

- Installation image: <https://archlinux.org/download/>

```shell
# Connect to Wi-Fi
iwctl
[iwd] device list
[iwd] station "device" get-networks
[iwd] station "device" connect "ssid"
ping archlinux.org

# Update system clock
timedatectl set-ntp true

# Partitions
lsblk
fdisk -l # Optionally use cgdisk
mkfs.vfat "/dev/sdx1" # efi partition (use 300 MB)
mkfs.ext4 "/dev/sdx2" # root partition
mkfs.ext4 "/dev/sdx3" # home partition

# Swap
mkswap "/dev/sdx4" # swap partition
dd if="/dev/zero" of="/swapfile" bs="1M" count="1024" status="progress" # 1GB swap file (only for UEFI systems)
chmod 600 "/swapfile"
mkswap "/swapfile"
swapon "/dev/sdx4" # or /swapfile

# Mount partitions
mount "/dev/sdx2" "/mnt" # root
mkdir "/mmt/{boot,home}"
mount "/dev/sdx1" "/mnt/boot" # boot/efi
mount "/dev/sdx3" "/mnt/home" # home
df -h # Show mounted partitions

# Select mirrors
vi "/etc/pacman.d/mirrorlist"
pacman -Syy # Test mirrors

# Install system
pacstrap "/mnt" "base" "base-devel" "linux" "linux-firmware" "linux-headers"

# Generate fstab
genfstab -U "/mnt" >> "mnt/etc/fstab" # fstab for partitions mounted at /mnt

# Chroot
arch-chroot "/mnt"

# Region
ln -sf "/usr/share/zoneinfo/Region/City" "/etc/localtime"
hwclock --systohc

# Language
sed -i '177s/.//' /etc/locale.gen # Edit /etc/locale.gen
locale-gen
echo "LANG=en_US.UTF-8" >> /etc/locale.conf # Create /etc/locale.conf

# Hostname and hosts
echo "yourhostname" >> /etc/hostname
echo "127.0.0.1 localhost" >> /etc/hosts
echo "::1 localhost" >> /etc/hosts
echo "127.0.1.1 arch.localdomain arch" >> /etc/hosts

# Root password
passwd
root:password | chpasswd # optional

# Install additional packages
pacman -S "grub" "efibootmgr" "os-prober" # boot
pacman -S  "intel-ucode" "mesa" "nvidia" "nvidia-utils" "nvidia-settings" "nvidia-prime" "networkmanager" "bluez" "bluez-utils" # firmware
pacman -S "vim" "zsh" # Utilities
pacman -S "gnome" # (optional)

# Install grub
mount "/dev/sdx1" "/boot"
grub-install --target="x86_64-efi" --efi-directory="/boot" --bootloader-id="GRUB"
grub-mkconfig -o "/boot/grub/grub.cfg"

# Create user
useradd -m -d "/home/hvitoi" -s "/bin/zsh" "hvitoi"
usermod -aG "wheel" "hvitoi"
passwd "hvitoi"

# Configure sudo for the user
EDITOR=vim visudo # Uncomment %wheel ALL=(ALL) ALL

# Enable services
systemctl enable "gdm.service" # for gnome only
systemctl enable "NetworkManager.service"
systemctl enable "bluetooth.service"

# Unmount everything
umount -a

# Reboot (first exit chroot)
reboot
```

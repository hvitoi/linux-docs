# mkswap

- Swap space is used when the RAM memory is full
- Swap is localted in the local hard drive and therefore it's slow

## Create swap file

```bash
# Create swap file
sudo dd \
  if=/dev/zero \ # Read from file (instead of standard input)
  of=/media/hvitoi/Dummy/swapfile \ # Write to a file (instead of standard output)
  bs=1M \
  count=4G # Total size of the file 4194304 = 4096M = 4G
# Swap cannot be created via touch command because this way it would be an empty file

# Remove rwx permissions from other users
sudo chmod 600 /media/hvitoi/Dummy/swapfile # chmod go-r file

# Make swap out of the swap file
sudo mkswap /media/hvitoi/Dummy/swapfile

# Activate swap
sudo swapon /media/hvitoi/Dummy/swapfile

# Show the swap areas
sudo swapon --show
free -m

# Remove swap
swaooff /media/hvitoi/Dummy/swapfile
rm /media/hvitoi/Dummy/swapfile
```

## Create swap from a partition

```bash
# Disable all swap memories
swapoff -a


# Display all partition on the drive
fdisk -l

# Form the partition into a swap partition via fdisk interative shell
fdisk /dev/sdx

# Force the kernel to re-read the partition and add it to swap
partprobe

# Make the swap
mkswap /dev/sdc

# Add the swap partition to the fstab
sudo nano /etc/fstab

# Activate swap
swapon -a
```

## Add swap to fstab

- Configure the `/etc/fstab`

```fstab
# <file system> <mount point> <type> <options> <dump> <pass>

# Debian
UUID=027f36af-e4d6-4903-993b-cd0176d2699e / ext4 errors=remount-ro 0 1

# EFI
UUID=103C-FD10 /boot/efi vfat umask=0077 0 1

# Swap
UUID=c0ebb46b-89d1-42fc-9af7-e4394d27c24e none swap sw 0 0
#/media/hvitoi/Dummy/swapfile none swap sw 0 0

# Moon
UUID=C2D8DF53D8DF43F7 /media/hvitoi/Moon ntfs defaults,uid=1000 0 0
```

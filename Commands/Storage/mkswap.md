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
swapon /dev/sdx # activate specific swap
```

- `echo '/swapfile none swap sw 0 0' | tee -a /etc/fstab`
- Append new swap item to fstab (only if created after the genfstab command)

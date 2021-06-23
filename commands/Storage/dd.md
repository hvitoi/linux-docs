# dd

- Used for system backups
- 5 types of backup

  1. `System backup`: entire image (acronis, veeam, commvault, etc )
  1. `Application backup`: for a specific app (3rd party software)
  1. `Database backup`: database (oracle dataguard, sql backup, etc)
  1. `Filesystem backup`: filesystem copy (tar, gzip, directoris, etc)
  1. `Disk backup or disk cloning`: Clones the disk (dd command)

- `dd` primary purpose is to convert and copy files!
- `dd` doesn't care about the size used! It copies everything (used and free memory)

```shell
dd if=`src-file` of=`dest-file`
dd if=/dev/sdx of=/dev/sdy # Copy disk to disk
dd if=/dev/sdx of=/data # Copy disk to directory

dd if=/dev/sdx1 of=/dev/sdy1 # Copy partition to partition
dd if=/dev/sdx1 of=/data/sdx1.img # Copy partition to file

dd if=/data/sdx1.img of=/dev/sdx1 # Restory backup from file
```

## Copy ISO to flash drive

```shell
## List block devices
lsblk

## Unmount the partition
sudo umount /dev/sdx1

## Copy and convert files to flash drive
sudo dd \
  if=input.iso \
  of=/dev/sdx \
  bs=4M \
  conv=fdatasync \
  status=progress
```

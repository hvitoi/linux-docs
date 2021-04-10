# mkfs

- Make file system for a partition

```sh
# Make a XFS partition
mkfs.xfs `partition`
mkfs.xfs /dev/sdx1
mount /dev/sdx1 /data

# Make a EXT4 partition
mkfs.ext4 `partition`
mkfs.ext4 /dev/sdx1
mount /dev/sdx1 /data
```

## Remove reserved space

- Reserved space can be removed from ext4 filesystems if you don't plan to install the system there

```sh
tune2fs -m 0 "/dev/sdx1"
```
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

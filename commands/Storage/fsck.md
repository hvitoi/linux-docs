# fsck

- Linux fsck utility is used to check and repair Linux filesystems
- EXT2, EXT3, EXT4, etc
- The system sometimes run fsck during `boot time` to check whether the fs is in consistent state
- fsck must be run in `unmounted` file systems! To avoid data corruption
- fsck is run on the `filesystem`, not on the mounted on

```sh
fsch /dev/sdx1
fsch /dev/sdx1 -f # force system check even if it is clean
fsch /dev/sdx1 -y # fix problems automatically

```

- `Exit codes` for fsck. `echo $?` to see the code
  - `0`: No errors
  - `1`: fs errors corrected
  - `2`: system must be rebooted
  - `4`: fs errors left uncorrected
  - `8`: operational error
  - `16`: usage or syntax error
  - `32`: fsck canceled by user request
  - `128`: Shared-library error

## xfs_repair

- Similar to fsck but for XFS file systems
- Unlike fsck, it does not run at boot time
- For large partitions. Terabytes

```sh
# Unmount the filesystem first
umount /data # /data is the folder in which the FS is mounted

# Repair
xfs_repair `filesystem`
xfs_repair /dev/sdx1

# Mount it back
mount /dev/sdx1 /data
```

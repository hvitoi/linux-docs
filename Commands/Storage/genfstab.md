# genfstab

- Generate fstab file

```sh
# By UUID
genfstab -U /mnt >> /mnt/etc/fstab

# By Labels
genfstab -L /mnt >> /mnt/etc/fstab
```

## Add swap to fstab

- Configure the `/etc/fstab`

```conf
# Static information about the filesystems.
# See fstab(5) for details.

# <file system> <dir> <type> <options> <dump> <pass>
# /dev/sdb3 - Archlinux
UUID=073ff8d8-a99f-4397-8413-3201c6544a9b	/			ext4	rw,relatime		0	1

# /dev/sdc - Swap
UUID=88237e2c-f3fb-4056-966b-e39f137a1736	none			swap	defaults		0	0

# /dev/sda1 - Moon
UUID=C2D8DF53D8DF43F7				/media/hvitoi/Moon	ntfs	defaults,uid=1000	0	0
```
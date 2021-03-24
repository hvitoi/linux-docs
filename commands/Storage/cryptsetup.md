# cryptsetup

- Create an empty partition (with no filesystem)

## LUKS Format

```sh
# First make sure no partitions are created in the drive (free space)
cryptsetup luksFormat "/dev/sdx"
```

## Open/Unlock drive

- Opened/unlocked drives are mapped to `/dev/mapper/drive-name`
- Once opened, you it's completely treated as any other hard drive

```sh
cryptsetup luksOpen "/dev/sdx" "drive-name"
```

## Create filesystem

- Filesystem can be created inside the unlocked container
- mkfs at that point doesn't know it was an encrypted drive. It treats like any other storage device

```sh
mkfs.exfat "/dev/mapper/drive-name"
mkfs.ext4 "/dev/mapper/drive-name"
```

```sh
# Other commands on the unlocked drive
fsck "/dev/mapper/drive-name"
mount "/dev/mapper/drive-name" "/mnt/data"
```

## LUKS header

```sh
# Show LUKS header unformation (including key slots/passwords)
cryptsetup luksDump "/dev/sdx1"

# Backup or Restore the LUKS header (it's very important because if the header is corrupted, the whole disk is corrupted)
cryptsetup luksHeaderBackup "/dev/sdx1" --header-backup-file "LuckyHeader.bin" # Backup
cryptsetup luksHeaderRestore "/dev/sdx1" --header-backup-file "LuckyHeader.bin" # Restore
```

## LUKS passwords

```sh
# Change password (this will look if the old password exists, if yes then replace it)
cryptsetup luksChangeKey "/dev/sdx1"

# Add new key to new key slow
cryptSetup luksAddKey "/dev/sdx1"
```

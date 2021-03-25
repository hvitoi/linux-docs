# cryptsetup

- Create an empty partition (with no filesystem)

## Format and encrypt a partition

```sh
# A partition or the whole disk can be encrypted
cryptsetup luksFormat "/dev/sdx" # or /dev/sdx1 for a single partition
cryptsetup luksFormat "/dev/sdx" --verbose --verify-passphase
```

## Unlock/Lock drive

- Unlocked drives are mapped to `/dev/mapper/drive-name`
- Once opened, you it's completely treated as any other hard drive

```sh
# Unlock
cryptsetup luksOpen "/dev/sdx" "drive-name" # /dev/sdx1 to open a partition

# Lock
cryptsetup luksClose "drive-name"
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

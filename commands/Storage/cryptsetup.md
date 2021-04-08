# cryptsetup

- `dm-crypt` is the Linux kernel's device mapper crypto target

## Prepare the disk

```sh
# Create a temporary encrypted container to be cleaned
cryptsetup open \
  --type "plain" \
  -d "/dev/urandom" \
  "/dev/sdx" "to_be_wiped"

# Wipe the container with zeroes
dd \
  if="/dev/zero" \
  of="/dev/mapper/to_be_wiped" \
  status="progress"

# Close container
cryptsetup close "to_be_wiped"
```

## Format and encrypt a partition

```sh
# A partition or the whole disk can be encrypted
cryptsetup luksFormat "/dev/sdx" # or /dev/sdx1 for a single partition
cryptsetup luksFormat "/dev/sdx" --verbose --verify-passphase # -v -y
```

## Unlock/Lock drive

- Unlocked drives are mapped to `/dev/mapper/drive-name`
- Once opened, you it's completely treated as any other hard drive

```sh
# Unlock
cryptsetup open "/dev/sdx" "drive-name" # Drive is mapped to /dev/mapper/drive-name

# Lock
cryptsetup close "drive-name"
```

## Create filesystem

- Filesystem can be created inside the unlocked container
- mkfs doesn't know it is an encrypted drive. It treats like any other storage device

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
# Show LUKS header information (including key slots/passwords)
cryptsetup luksDump "/dev/sdx1"

# Backup or Restore the LUKS header (if the header is corrupted, the whole disk is corrupted)
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

## crypttab

- `etc/crypttab` (encrypted device table) file is similar to the `fstab` file and contains a list of encrypted devices to be unlocked during system boot up. This file can be used for automatically mounting encrypted swap devices or secondary file systems
- `crypttab` is read before `fstab`, so that `dm-crypt` containers can be unlocked before the file system inside is mounted
- crypttab processing at boot time is made by the `systemd-cryptsetup-generator`
- `noauto` param mounts on demand

```sh
# get UUID of the encrypted device
cryptsetup luksUUID "/dev/sdx"
```

```crypttab
moon UUID=692e7b5c-5c92-4fd3-8822-97b0355c0941 none luks
```

```fstab
/dev/mapper/moon  /media/hvitoi/moon  exfat defaults,uid=1000  0 2
```

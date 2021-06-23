# cryptsetup

- `Cryptsetup` is the command line tool to interface with `dm-crypt` for creating, accessing and managing encrypted devices.
- The tool was later expanded to support different encryption types that rely on the Linux kernel **d**evice-**m**apper and the **crypt**ographic modules.
- The most notable expansion was for the `Linux Unified Key Setup (LUKS)` extension, which stores all of the needed setup information for dm-crypt on the disk itself

## Prepare the disk

```shell
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

```shell
# A partition or the whole disk can be encrypted
cryptsetup luksFormat "/dev/sdx" # or /dev/sdx1 for a single partition
cryptsetup luksFormat "/dev/sdx" --verbose --verify-passphase # -v -y
```

## Unlock/Lock drive

- Unlocked drives are mapped to `/dev/mapper/drive-name`
- Once opened, you it's completely treated as any other hard drive

```shell
# Unlock
cryptsetup open "/dev/sdx" "drive-name" # Drive is mapped to /dev/mapper/drive-name

# Lock
cryptsetup close "drive-name"
```

## Create filesystem

- Filesystem can be created inside the unlocked container
- mkfs doesn't know it is an encrypted drive. It treats like any other storage device

```shell
mkfs.exfat "/dev/mapper/drive-name"
mkfs.ext4 "/dev/mapper/drive-name"
```

```shell
# Other commands on the unlocked drive
fsck "/dev/mapper/drive-name"
mount "/dev/mapper/drive-name" "/mnt/data"
```

## LUKS header

```shell
# Show LUKS header information (including key slots/passwords)
cryptsetup luksDump "/dev/sdx1"

# Backup or Restore the LUKS header (if the header is corrupted, the whole disk is corrupted)
cryptsetup luksHeaderBackup "/dev/sdx1" --header-backup-file "LuckyHeader.bin" # Backup
cryptsetup luksHeaderRestore "/dev/sdx1" --header-backup-file "LuckyHeader.bin" # Restore
```

## LUKS passwords

```shell
# Change password (this will look if the old password exists, if yes then replace it)
cryptsetup luksChangeKey "/dev/sdx1"

# Add new key to new key slow
cryptSetup luksAddKey "/dev/sdx1"
```

## crypttab

- `/etc/crypttab` (encrypted device table) file is similar to the `fstab` file and contains a list of encrypted devices to be unlocked during system boot up. This file can be used for automatically mounting encrypted swap devices or secondary file systems
- `crypttab` is read before `fstab`, so that `dm-crypt` containers can be unlocked before the file system inside is mounted
- crypttab processing at boot time is made by the `systemd-cryptsetup-generator`
- `noauto` param mounts on demand

```shell
# get UUID of the encrypted device
cryptsetup luksUUID "/dev/sdx"
```

```crypttab
moon UUID=692e7b5c-5c92-4fd3-8822-97b0355c0941 none luks
```

```fstab
/dev/mapper/moon  /media/hvitoi/moon  exfat defaults,uid=1000  0 2
```

## Mounting at login

- It is possible to configure `PAM` and `systemd` to automatically mount a dm-crypt encrypted home partition when its owner logs in, and to unmount it when they log out

- **To unlock at login**

  - Edit `/etc/pam.d/system-login`

  ```conf
  ...
  auth       include    system-auth
  auth       optional   pam_exec.so expose_authtok /etc/pam_cryptsetup.sh
  ...
  ```

  - Create the script `/etc/pam_cryptsetup.sh` and make it executable `chmod +x script.sh`

  ```shell
  #!/usr/bin/env bash

  CRYPT_USER="hvitoi"
  PARTITION="/dev/sdx"
  NAME="moon-$CRYPT_USER"

  if [[ "$PAM_USER" == "$CRYPT_USER" && ! -e "/dev/mapper/$NAME" ]]; then
      /usr/bin/cryptsetup open "$PARTITION" "$NAME"
  fi
  ```

- **To mount/unmount at login/logout**

  - Create file `/etc/systemd/system/media-hvitoi-moon.mount`
  - Enable it `systemctl enable media-hvitoi-moon.mount`

  ```conf
  [Unit]
  Requires=user@1000.service
  Before=user@1000.service

  [Mount]
  Where=/media/hvitoi/moon
  What=/dev/mapper/moon
  Type=ext4
  Options=defaults,relatime

  [Install]
  RequiredBy=user@1000.service
  ```

- **To lock at logout**

  - Create file `/etc/systemd/system/cryptsetup-hvitoi.service`
  - Enable it `systemctl enable cryptsetup-hvitoi.service`

  ```conf
  [Unit]
  DefaultDependencies=no
  BindsTo=dev-sda.device
  After=dev-sda.device
  BindsTo=dev-mapper-moon.device
  Requires=media-hvitoi-moon.mount
  Before=media-hvitoi-moon.mount
  Conflicts=umount.target
  Before=umount.target

  [Service]
  Type=oneshot
  RemainAfterExit=yes
  TimeoutSec=0
  ExecStop=/usr/bin/cryptsetup close moon

  [Install]
  RequiredBy=dev-mapper-moon.device
  ```

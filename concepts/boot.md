# Linux boot

## System Run Level

- 7 run levels

  1. `Run level 0`: Shut down (or halt the system)
  1. `Run level 1`: Single-user mode; usually aliased as s or S
  1. `Run level 2`: Multiuser mode without networking
  1. `Run level 3`: Multiuser mode with networking (without GUI)
  1. `Run level 4`: Currently undefined
  1. `Run level 5`: Multiuser mode with networking (with GUI)
  1. `Run level 6`: Reboot the system

- 0, 1 and 6 are the main run levels

```shell
# Tells the current run level of the session
who -r # Usually 5 (networking with gui)
```

```shell
# Set default run level (5 by default)
systemctl set-default `new-target`
```

- Default target stored at `/etc/systemd/system/default.target`

## Linux Boot Process

1. **BIOS**: Basic Input/Output Setting
   - It's a `firmware` interface
   - `System integrity` checks
   - Find out how to boot
   - `POST` process: Power-On Self-Test started
1. **MBR**: Master Boot Record executes GRUB
   - Located in the `first sector` of the disk
   - Bytes in size (small)
   - Calls the GRUB2, so it can be loaded in the computer RAM
1. **GRU2B**: Grand Unified Bootloader x2
   - Load the linux kernel
   - Config file: `/boot/grub2/grub.cfg`
1. **Kernel**: Core of the Operating System
   - Load required drivers from `initrd.img`
   - Mounts the root filesystem
   - Start the first OS process (`systemd`)
1. **Systemd**: System Daemon (PID #1)
   - Start all the other required processes
   - Reads `/etc/systemd/system/default.target` to bring the system to run-level

## Message of the day

- Located at `/etc/motd`

```txt
The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
```

- Customize the message of the day
- Create a new file for the scripts in `/etc/profile.d/motd.sh`

```bash
#!/bin/bash

echo -e "
Welcome to `hostname`
This system is runing `cat /etc/debian_version`
Kernel is `uname -r`
You are logged in as `whoami`
"
```

- Modify the `/etc/ssh/sshd_config` to edit `PrintMotd`

```conf
PrintMotd no
```

```shell
# Restart sshd service
systemctl restart sshd
```

## Grub

### Installation

```shell
# Arch
pacman -S "grub" "efibootmgr" "os-prober"
mount "/dev/sdx1" "/boot"
grub-install --target="x86_64-efi" --efi-directory="/boot" --bootloader-id="GRUB"
grub-mkconfig -o "/boot/grub/grub.cfg"
```

```shell
# Non-arch
sudo mount "/dev/sdx3" "/mnt"
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt

mount "/dev/sda1" "/boot"
grub-install "/dev/sda"
update-grub
```

## Recover root password

1. Restart PC
1. On grub, highlight the linux system and press `e` to edit it
1. Replace the `ro` (read only) with `rw init=/sysroot/bin/sh`
1. Ctrl + X (The computer will restart in single user mode)
1. Type `chroot /sysroot` (mount the filesystem to /sysroot)
1. Type `passwd root`
1. Type `touch /.autorelabel`
1. Type `exit && reboot`

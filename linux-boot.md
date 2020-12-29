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

```sh
# Tells the current run level of the session
who -r # Usually 5 (networking with gui)
```

```sh
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

- Restart sshd service

```sh
systemctl restart sshd
```

## Grub repair

### Change root

```bash
sudo mount /dev/sda3 /mnt
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
```

### Install grub

```bash
mount /dev/sda1 /boot/efi
grub-install /dev/sda
update-grub
```

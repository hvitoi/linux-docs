# Recover root password

1. Restart PC
1. On grub, highlight the linux system and press `e` to edit it
1. Replace the `ro` (read only) with `rw init=/sysroot/bin/sh`
1. Ctrl + X (The computer will restart in single user mode)
1. Type `chroot /sysroot` (mount the filesystem to /sysroot)
1. Type `passwd root`
1. Type `touch /.autorelabel`
1. Type `exit && reboot`

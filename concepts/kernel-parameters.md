# Kernel Parameters

- Check the parameters your system was booted up with at `/proc/cmdline`

```txt
BOOT_IMAGE=/boot/vmlinuz-linux root=UUID=2740a3e6-85af-4d4a-bf60-242614758599 rw loglevel=3 quiet
```

## Add parameters via grub

- Press `e` when the menu shows up and add them on the linux line
- Press Ctrl+x to boot with these parameters.

```txt
linux /boot/vmlinuz-linux root=UUID=0a3407de-014b-458b-b5c1-848e92a327a3 rw quiet splash
```

- To make the change persistent after reboot, edit `/etc/default/grub` and append your kernel options between the quotes in the `GRUB_CMDLINE_LINUX_DEFAULT` line

```conf
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1"
```

= And then automatically re-generate the `grub.cfg` file with:

```sh
grub-mkconfig -o /boot/grub/grub.cfg
```

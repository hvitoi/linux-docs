# Additional packages

## Base

- `base`: Minimal package set to define a basic Arch Linux installation
- `base-devel`: Building tools
  1. autoconf
  2. automake
  3. binutils
  4. bison
  5. fakeroot
  6. file
  7. findutils
  8. flex
  9. gawk
  10. gcc
  11. gettext
  12. grep
  13. groff
  14. gzip
  15. libtool
  16. m4
  17. make
  18. pacman
  19. patch
  20. pkgconf
  21. sed
  22. sudo
  23. texinfo
  24. which
- `linux`: The Linux kernel and modules (Optionally use linux-lts)
- `linux-firmware`: Firmware files for Linux
- `intel-ucode`: Stability and security updates for Intel CPUs
- `grub`: GNU GRand Unified Bootloader
- `efibootmgr`: Linux user-space application to modify the EFI Boot Manager
- `os-prober`:Utility to detect other OSes on a set of drives
- `bluez`: Daemons for the bluetooth protocol stack
- `bluez-utils`: Development and debugging utilities for the bluetooth protocol stack
- `gnome`: GUI

```sh
systemctl enable gdm.service
systemctl enable NetworkManager.service
systemctl enable bluetooth.service
```

## Packages

- `vim`
- `pavucontrol`
- `solaar`
- `ttf-droid`
- `tilix`
- `cmatrix`
- `vlc`
- `gimp`
- `drawing`
- `inkscape`
- `handbrake`
- `qbittorrent`
- `obs-studio`
- `texstudio`
- `texlive-core`
- `grub-customizer`
- `chntpw`
- `ntfs-3g`
- `exfat-utils`
- `mesa`
- `chrome-gnome-shell`

## AUR

- `google-chrome`
- `visual-studio-code-bin`
- `snapd`
- `spotify`
- `teams`
- `drawio-desktop`
- `google-earth-pro`
- `popcorntime-bin`
- `f5vpn`
- `pulseaudio-modules-bt`

## Dev

- `jdk11-openjdk`
- `nodejs`
- `npm`
- `kubectl`
- `docker`
- `docker-compose`
- `librdkafka`
- `avro-c` (AUR)
- `kafkacat` (AUR)
- `k9s`
- `postman-bin` (AUR)
- `skaffold`
- `github-desktop-bin` (AUR)
- `minikube`
- `intellij-idea-community-edition`

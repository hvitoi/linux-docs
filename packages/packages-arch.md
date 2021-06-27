# Additional packages

## Base

- `base`: Minimal package set to define a basic Arch Linux installation
- `base-devel`: Building tools
- `linux`: The Linux LTS kernel and modules
- `linux-firmware`: Firmware files for Linux
- `linux-headers`: Headers and scripts for building modules for the Linux kernel

## Boot

- `grub`: GNU GRand Unified Bootloader
- `efibootmgr`: Linux user-space application to modify the EFI Boot Manager
- `os-prober`:Utility to detect other OSes on a set of drives

## Firmware

- `intel-ucode`: Stability and security updates for Intel CPUs
- `mesa`
- `nvidia`: NVIDIA drivers
- `nvidia-utils`: NVIDIA utils
- `nvidia-settings`: Tool for configuring the NVIDIA graphics driver
- `nvidia-prime`
- `networkmanager`: networking
- `bluez`: Daemons for the bluetooth protocol stack
- `bluez-utils`: Development and debugging utilities for the bluetooth protocol stack
- `aic94xx-firmware` (AUR)
- `wd719x-firmware` (AUR)
- `upd72020x-fw` (AUR)

## Audio

- `pipewire`
- `pipewire-docs`: only for documentation, not necessary
- `pipewire-alsa`
- `pipewire-pulse`
- `pipewire-jack`
- `xdg-desktop-portal`: screen sharing on browsers
- `xdg-desktop-portal-gtk`: screen sharing on browsers with gnome
- `xdg-desktop-portal-wlr`: screen sharing on browsers with wayland root
- `gst-plugin-pipewire`: need if using xdg-desktop-portal-wlr
- `pulseaudio`
- `pulseaudio-alsa`
- `pulseaudio-jack`

## GUI

- `sway`: Window Manager for Wayland (alternative to xorg i3)
- `swaylock`: lock screen
- `swayidle`
- `xorg-xwayland`: compatibility layer between xorg and wayland
- `dmenu`: menu bar
- `gdm`: graphical display manager. Enable gdm.service
- `ly-git` (AUR): console display manager. Enable ly.service

## Fonts

- `ttf-droid`
- `ttf-font-awesome`

## Utilities

- `vim`
- `oh-my-zsh` (BIN)
- `ntfs-3g`: Support for NTFS filesystem
- `dmidecode`
- `dnsutils`
- `chntpw`
- `htop`
- `grub-customizer`
- `exfatprogs`: Preferred over exfat-utils (deprecated). ln -s "/usr/sbin/mkfs.exfat" "/usr/local/sbin/mkexfatfs"
- `tilix`
- `alacritty`: default terminal in sway
- `gnome-tweaks`
- `pulseaudio-modules-bt-git` (AUR)
- `woeusb` (AUR)
- `f5vpn` (AUR)
- `networkmanager-f5vpn` (AUR): NetworkManager plugin for f5 vpn
- `net-tools`
- `wireshark-qt`
- `rclone`
- `nmap`
- `gparted`
- `veracrypt`
- `chrome-gnome-shell`: gnome shell integration with web browsers
- `ffmpegthumbnailer`: video thumbnail support
- `gst-libav`: video thumbnail support
- `gst-plugins-ugly`: video thumbnail support
- `networkmanager-openconnect`: vpn client
- `jq`: JSON parsing
- `diffpdf`
- `git-latexdiff`
- `fdupes`: find duplicate files
- `testdisk`: data recovery utility
- `unrar`: winrar
- `pdfarrange`: pdf manipulation
- `paru`: wrapper on pacman
- `bitwarden` (AUR): password manager

## I/O

- `i2c-tools`
- `ddcutil`
- `solaar`
- `v4l2loopback-dkms`
- `droidcam` (BIN)
- `virtualbox`
- `virtualbox-host-modules-arch`
- `pavucontrol`

## Development

- `visual-studio-code-bin` (AUR)
- `curl`
- `jdk11-openjdk`
- `git`
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
- `helm`
- `android-tools`
- `azure-cli` (AUR)
- `azure-functions-core-tools-bin` (AUR)
- `dotnet-sdk`
- `nuget`
- `mono`
- `gitkraken` (AUR)
- `diffutils`
- `freerdp`
- `powershell-bin` (AUR)
- `dbeaver`
- `kafka` (AUR)
- `cmake`
- `python`
- `python-pip`
- `nvm` (AUR)
- `rust`
- `go`
- `istio`
- `filezilla`
- `ngrok` (AUR): expose your localhost
- `mycli` (AUR): MySQL CLI with autocomplete
- `robo3t-bin` (AUR): MongoDB UI
- `maven`: java package manager
- `tomcat10`

## Apps

- `firefox`
- `vlc`
- `gimp`
- `drawing`
- `inkscape`
- `handbrake`
- `qbittorrent`
- `obs-studio`
- `libreoffice-fresh`
- `google-chrome` (AUR)
- `spotify` (AUR)
- `teams` (AUR)
- `slack-desktop` (AUR)
- `drawio-desktop` (AUR)
- `google-earth-pro` (AUR)
- `popcorntime-bin` (AUR)
- `cmatrix`
- `texstudio`
- `texlive-most`
- `discord`
- `typora` (AUR)

## Others

- `network-manager-applet`
- `dialog`
- `wpa_supplicant`
- `mtools`
- `dosfstools`
- `reflector`
- `avahi`
- `xdg-user-dirs`
- `xdg-utils`
- `gvfs`
- `gvfs-smb`
- `nfs-utils`
- `inetutils`
- `dnsutils`
- `cups`
- `hplip`
- `alsa-utils`
- `bash-completion`
- `openssh`
- `rsync`
- `reflector`
- `acpi`
- `acpi_call`
- `tlp`
- `virt-manager`
- `qemu`
- `qemu-arch-extra`
- `edk2-ovmf`
- `bridge-utils`
- `dnsmasq`
- `vde2`
- `openbsd-netcat`
- `iptables-nft`
- `ipset`
- `firewalld`
- `flatpak`
- `sof-firmware`
- `nss-mdns`
- `acpid`
- `terminus-font`

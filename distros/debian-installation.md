# Debian ISO

- Debian Bullseye
- Testing branch
- Non-free repositories

<https://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/weekly-builds/amd64/iso-dvd/>

## Firmware drivers

- Firmwares are stored at `/lib/firmware`

### Non-free drivers for Asus Q550LF

- firmware-iwlwifi
- firmware-realtek
- intel-microcode
- firmware-misc-nonfree
- nvidia-driver (requires linux-headers-amd64)

### Firmware info

```bash
## List out missing drivers
sudo update-initramfs -u

# List out all non-free drivers - dpkg-query
dpkg-query -W -f='${Section}\t${Package}\n' | grep ^non-free

# List out all non-free drivers - aptitude
aptitude search '~i ?section(non-free)'
```

### Nvidia drivers

```bash
# Install
sudo apt install linux-headers-amd64 nvidia-driver

# Uninstall
apt purge *nvidia*
systemctl reboot
apt install --reinstall xserver-xorg-core xserver-xorg-video-nouveau
```

- Download from <https://www.debian.org/distrib/packages>

### Bumblebee

- Allows the use of NVIDIA Optimus both on `nvidia` or `nouveau` drivers

```sh
# Nouveau
sudo apt install bumblebee primus

# Nvidia
sudo apt install bumblebee-nvidia primus
```

### config iwlwifi

- /etc/modprobe.d/iwlwifi.conf

```conf
options iwlwifi bt_coex_active=0
```

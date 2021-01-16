# droicam

## Install droidcam client

```sh
cd /tmp/
wget -O droidcam_latest.zip https://files.dev47apps.net/linux/droidcam_1.7.1.zip
# sha1sum: c687253a17ca6a2337b85ed90de585c776174250
unzip droidcam_latest.zip -d droidcam
cd droidcam && sudo ./install-client
```

```sh
# Run droidcam client
droidcam
```

## Install ADB

```sh
# Install
sudo apt install adb

# Test
adb devices # must be in File Transfer mode
```

## Activate kernel module v4l2loopback

```sh
# Load loopback device temporarely
sudo modprobe v4l2loopback exclusive_caps=1 max_buffers=2

# Install dkms module
sudo apt install v4l2loopback-dkms v4l2loopback-utils
```

- Load module permanentely upon startup

```sh
# Config file
echo "v4l2loopback" >> /etc/modules-load.d/v4l2loopback.conf
```

- Load configuration

```sh
# Config file
echo "options v4l2loopback exclusive_caps=1" >> /etc/modprobe.d/v4l2loopback.conf
```

- Update initial ramdisk

```sh
sudo update-initramfs -u
```

- Check if the module is correctly active

```sh
lsmod | grep v4l2loopback
```

## Activate sound

```sh
# Load loopback device temporarely (optional)
modprobe snd-aloop
```

- Load module permanentely upon startup

```sh
# Config file
echo "snd-aloop" >> /etc/modules-load.d/snd-aloop.conf
```

- Load configuration

```sh
LOOPBACK_CARD_ID=$(grep -F "[Loopback" < /proc/asound/cards | awk '{print $1}')
echo "options snd-aloop index=$LOOPBACK_CARD_ID" >> /etc/modprobe.d/snd-aloop.conf # Config file
```

- Edit `/etc/pulse/default.pa` to show up the right audio device in PulseAudio
  - Uncomment line `load-module module-alsa-source device=hw:0,0`

```sh
# Determine the card and the device number of your mic
arecord -l

# Restart PulseAudio
pulseaudio -k ; pulseaudio -D
```

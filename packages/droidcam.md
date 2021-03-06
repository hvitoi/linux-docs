# droidcam

## Install droidcam client

```shell
cd /tmp/
wget -O droidcam_latest.zip https://files.dev47apps.net/linux/droidcam_1.7.1.zip
# sha1sum: c687253a17ca6a2337b85ed90de585c776174250
unzip droidcam_latest.zip -d droidcam
cd droidcam && sudo ./install-client
```

```shell
# Run droidcam client
droidcam
```

## Install ADB

```shell
# Install
sudo apt install adb

# Test
adb devices # must be in File Transfer mode
```

## Activate kernel module v4l2loopback

```shell
# Load loopback device temporarely
sudo modprobe v4l2loopback exclusive_caps=1 max_buffers=2

# Install dkms module
sudo apt install v4l2loopback-dkms v4l2loopback-utils
sudo pacman -S v4l2loopback-dkms
```

- Load module permanentely upon startup

```shell
# Config file
echo "v4l2loopback" >> /etc/modules-load.d/v4l2loopback.conf
```

- Load configuration

```shell
# Config file
echo '
# Module options for Video4Linux, needed for our DSLR Webcam
# alias dslr-webcam v4l2loopback
options v4l2loopback exclusive_caps=1
options v4l2loopback width=1920
options v4l2loopback height=1080
' \
>> /etc/modprobe.d/v4l2loopback.conf
```

- Update initial ramdisk

```shell
sudo update-initramfs -u
```

- Check if the module is correctly active

```shell
lsmod | grep v4l2loopback
```

## Activate sound

```shell
# Load loopback device temporarely (optional)
modprobe snd-aloop
```

- Load module permanentely upon startup

```shell
# Config file
echo "snd-aloop" >> /etc/modules-load.d/snd-aloop.conf
```

- Load configuration

```shell
LOOPBACK_CARD_ID=$(grep -F "[Loopback" < /proc/asound/cards | awk '{print $1}')
echo "options snd-aloop index=$LOOPBACK_CARD_ID" >> /etc/modprobe.d/snd-aloop.conf # Config file
```

- Edit `/etc/pulse/default.pa` to show up the right audio device in PulseAudio
  - Uncomment line `load-module module-alsa-source device=hw:0,0`
  - replace to `load-module module-alsa-source device=hw:Loopback,1,0`

```shell
pacmd load-module module-alsa-source device=hw:Loopback,1,0
```

```shell
# Determine the card and the device number of your mic
arecord -l

# Restart PulseAudio
pulseaudio --kill
pulseaudio --start
pulseaudio --daemonize
```

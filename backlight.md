# Backlight

- Power level of backlight LEDs can be controlled using `ACPI` kernel module
- `/sys/class/backlight/`
  - intel_backlight

## External monitor

### i2c-dev

- `i2c-dev` is the module to control external monitor brightness over I2C

```sh
modprobe i2c-dev # Manual one-time load
```

```conf
# /etc/modules-load.d/i2c-dev.conf
i2c-dev
```

- `i2c-tools` must be installed for a good integration

```sh
pacman -S i2c-tools
sudo groupadd --system i2c # create i2c group (if not exists already)
sudo cp /usr/share/ddcutil/data/45-ddcutils-i2c.rules /etc/udev/rules.d # Copy the udev rule for the new group to rules.d
usermod -aG i2c hvitoi  # add user to the i2c group
```

### ddcutil

- It's a backlight utility package that can be used to query and set brightness settings

```sh
pacman -S ddcutil
ddcutil capabilities # "Feature: 10" is brightness

# Brightness
ddcutil getvcp 10 # Get current brightness value
ddcutil setvcp 10 70 # Set brightness to 70

ddcutil environment
ddcutil detect
```

### ddccontrol

- `ddccontrol` is a GUI that relies on ddcutil
- Requires `ddccontrol-db-git`

### ddcci

- Package `ddcci-driver-linux-dkms` package for the module to expose external monitors in sysfs
- Monitor is exposed at `/sys/class/backlight/`
- Integrates well with gnome

```conf
# /etc/modules-load.d/ddcci.conf
ddcci
```

```sh
# Brightness slider
gdbus call --session --dest org.gnome.SettingsDaemon.Power --object-path /org/gnome/SettingsDaemon/Power --method org.freedesktop.DBus.Properties.Set org.gnome.SettingsDaemon.Power.Screen Brightness "<int32 75>"
gdbus call --session --dest org.gnome.SettingsDaemon.Power --object-path /org/gnome/SettingsDaemon/Power --method org.freedesktop.DBus.Properties.Get org.gnome.SettingsDaemon.Power.Screen Brightness

# Keyboard brightness
gdbus call --session --dest org.gnome.SettingsDaemon.Power --object-path /org/gnome/SettingsDaemon/Power --method org.gnome.SettingsDaemon.Power.Screen.StepUp
gdbus call --session --dest org.gnome.SettingsDaemon.Power --object-path /org/gnome/SettingsDaemon/Power --method org.gnome.SettingsDaemon.Power.Screen.StepDown

```

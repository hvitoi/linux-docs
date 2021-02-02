# Backlight

- Power level of backlight LEDs can be controlled using `ACPI` kernel module
- `/sys/class/backlight/`
  - intel_backlight

## External monitor

- `i2c-dev` is the module to control external monitor brightness over I2C
- `ddcutil` package can be used to query and set brightness settings

```sh
sudo modprobe i2c-dev
sudo pacman -S ddcutil
```

```sh
sudo ddcutil environment
sudo ddcutil detect
```

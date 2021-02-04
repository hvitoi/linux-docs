# Fix buzz sound when idle

- At `/etc/modprobe.d/modprobe.conf`

```conf
# Add this line
options snd_hda_intel power_save=0 power_save_controller=N
```

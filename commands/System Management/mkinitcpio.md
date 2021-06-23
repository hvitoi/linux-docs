# mkinitcpio

- mkinitcpio is a Bash script used to create an initial ramdisk environment (initramfs stage)
- The initial ramdisk is in essence a very small environment (early userspace) which loads various kernel modules and sets up necessary things before handing over control to init
- Config file `/etc/mkinitcpio.conf`

```shell
# All presets
mkinitcpio -P

# Only linux-lts
mkinitcpio -p linux-lts
```

- Missing hardware firmware will be shown in the initram

## Mkinitcpio modules

- The MODULES array is used to specify modules to load before anything else is done.
- `/etc/mkinitcpio.conf`
- And run mkinitcpio -P

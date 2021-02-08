# mkinitcpio

- mkinitcpio is a Bash script used to create an initial ramdisk environment
- The initial ramdisk is in essence a very small environment (early userspace) which loads various kernel modules and sets up necessary things before handing over control to init

```sh
# All presets
mkinitcpio -P

# Only linux-lts
mkinitcpio -p linux-lts
```

- Missing hardware firmware will be shown in the initram

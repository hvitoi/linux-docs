# init

```bash
# Shutdown
init 0

# Reboot and bring back in single user mode
init 1

# Just reboot
init 6
```

## System Run Level

- 6 run levels

  1. `Run level 0`: Shut down (or halt the system)
  1. `Run level 1`: Single-user mode; usually aliased as s or S
  1. `Run level 2`: Multiuser mode without networking
  1. `Run level 3`: Multiuser mode with networking (without GUI)
  1. `Run level 5`: Multiuser mode with networking (with GUI)
  1. `Run level 6`: Reboot the system

- 0, 1 and 6 are the main run levels
- 4 run level is undefined

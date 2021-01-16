# modprobe

- Add and remove modules from the Linux Kernel
- Loading kernel modules manually (through `modprobe`) means you will have to modprobe every time you reboot

```sh
modprobe `module-name`
modprobe bonding # And module for network bonding
modprobe v4l2loopback exclusive_caps=1 max_buffers=2 # virtual video devices

# Display configuration of the modules
modprobe -c
```

## Load module automatically

- To load modules upon start, modules must be defined in `/etc/modules`

```conf
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
bonding
v4l2loopback
```

- Optionally create a file at `/etc/modules-load.d/modulename.conf`
- E.g., `/etc/modules-load.d/v4l2loopback.conf` with the content v4l2loopback

```conf
# /etc/modules-load.d/v4l2loopback.conf
v4l2loopback
```

### Module default configuration

- Default configuration for the modules is stored at `/etc/modprobe.d` folder
  - E.g., `/etc/modprobe.d/v4l2loopback.conf`

```conf
options v4l2loopback exclusive_caps=1
```

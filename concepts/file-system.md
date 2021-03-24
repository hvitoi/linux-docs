# Linux File system

- `Linux File System` uses the `File Hierarchy Standard` (FHS) structure
- `Linux File System` examples: EXT3, EXT4, XFS

## File Hierarchy Standard

- `/boot`: Boot loader and memory test. grub.cfg, linux kernel, etc
- `/dev`: Devices (external devices connected to pc)
- `/etc`: Configuration files
- `/home`: Personal and configuration files related to one user
- `/media`: Mounting point for CD rooms and other external devices
- `/mnt`: Mount point for everything else
- `/opt`: Optional add-on apps. E.g., google chrome
- `/proc`: Info about running processes (virtual directory). Each folder represents a PID. It's emptied on shutdown
- `/root`: Root user home dir
- `/run`: Info about the current system state and system daemons in early stages (ex: systemd, udev) (virtual directory)
- `/srv`: Services. Designed to be accessible to other users (e.g., httpd public files)
- `/sys`: Firmwares (virtual directory)
- `/tmp`: Temporary files. Dummy files
- `/usr`: Useful files and programs for the user
  - `/bin`: User binaries (commands).
  - `/lib`: C libraries required by executable in /bin or /sbin (Multi-architecture).
  - `/sbin`: System binaries. Can only be run by root user. Ex: useradd.
  - `/local`: Programs installed by source code manually
- `/var`: System logs, backups, cache

## File attributes

- `d`: Directory
- `l`: Link
- `-`: File
- `c`: Special file / Device file (cpu, keyboard, memory ... )
- `s`: socket (ex: /dev/sda)
- `p`: Named pipe
- `b`: Block device

## Listing info in `ls -la`

| `type`     | `links` | `owner` | `group` | `size` | `month` | `day` | `time` | `name`     |
| ---------- | ------- | ------- | ------- | ------ | ------- | ----- | ------ | ---------- |
| drwxrwxrwx | 1       | hvitoi  | root    | 4096   | mar     | 22    | 2:52   | Javascript |

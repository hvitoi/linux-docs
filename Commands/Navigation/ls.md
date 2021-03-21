# ls - List

- `ls` is used for navigation through the `Linux File System`
- `Linux File System` uses the `File Hierarchy Standard` (FHS) structure
- `Linux File System` examples: EXT3, EXT4, XFS

## Linux File system

- `/boot`: Boot loader and memory test. grub.cfg
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
  - `/local`: Programs installed by source code
- `/var`: System logs, backups, cache

## Shell

- GNU BASH (Bourne-Again SHell) vs. GUI (Graphical User Interface)

## Dir listings attributes

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

## Listing

```bash
ls
ls -l
ls -la
ls -laF
ls -ltr # Time reverse order
ls -al / > lsout.txt # List the root dir and saves in the text file
ls -la /etc/cron.* # List the content of each folder starting with cron.
```

## Listing with wildcards

- Zero or more chars
  - `*` - `ls abc*`
- A single char
  - `?` - `ls ?bc*`
- Pick of characters
  - `[]` - `ls *[aeiou]*` # Either a, e, i, o, u
- Range of chars
  - `{}` - `touch abc{1..9}-xyz`
- Escape character
  - `\`
- Beginning of line
  - `^` - `ls -l | grep ^d` # List directories
- End of line
  - `$`
    `

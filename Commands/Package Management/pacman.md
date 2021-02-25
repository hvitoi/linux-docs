# pacman

- Mirrorlist stored at `/etc/pacman.d/mirrorlist`

## Query

```sh
# Query all packages
pacman --query
pacman -Q

# Explicitly installed
pacman -Qe

# AUR packages (foreign)
pacman -Qm

# Info about a package
pacman -Qi "package"
```

## Sync

```sh
# Install package
pacman --sync "package"
pacman -S "package"

# Refresh package database from server
pacman -Sy
pacman -Syy # force download (even if up to date)

# Upgrade installed packages
pacman -Su
pacman -Syu # update & upgrade

# Search package on remote repo
pacman -Ss "regex-package"
```

## Remove

```sh
# Remove package
pacman -R "package"

# Remote configuration files
pacman -Rn "package"

# Remove unnecessary dependencies
pacman -Rs

# Cascade (remove all packages that depend on them)
pacman -Rc "package"
```

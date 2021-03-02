# pacman

- Pacman settings `/etc/pacman.conf`
- Mirrorlist stored at `/etc/pacman.d/mirrorlist`
- Cache packages are stored at `/var/cache/pacman/pkg`

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

# List outdated packages
pacman -Qu
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

# Remove configuration files
pacman -Rn "package"

# Remove unnecessary dependencies
pacman -Rs

# Cascade (remove all packages that depend on them)
pacman -Rc "package"
```

## Modify

```sh
# Downgrade a kernel
pacman -U linux-4.15.8-1-x86_64.pkg.tar.xz
```

## IgnorePkg

- Skip package from being upgraded
- Add the packages to the at `/etc/pacman.conf`

```conf
IgnorePkg=linux
```

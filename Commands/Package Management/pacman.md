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
pacman -Rns "package"
pacman -Rcns "package" # Uninstall with all the dependencies

# Query
pacman -Q "package"
```

```sh
# Update repos
pacman -Syy
pacman -Syyy # including AUR

# Update packages
pacman -Syu
pacman -Syyu # including AUR
pacman -Syu --ignore "package" # Ignore a certain package


```

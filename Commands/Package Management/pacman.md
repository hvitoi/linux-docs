# pacman

- Mirrorlist stored at `/etc/pacman.d/mirrorlist`

```sh
# List installed
pacman -Qe # e for manually installed

# Install
pacman -S `package`

# Remove
pacman -R `package`
sudo pacman -Rns `package`

# Query
pacman -Q `package`
```

```sh
# Update repos
pacman -Syy

# Update packages
pacman -Syu
```
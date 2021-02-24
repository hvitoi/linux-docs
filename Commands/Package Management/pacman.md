# pacman

- Mirrorlist stored at `/etc/pacman.d/mirrorlist`

```sh
# List installed
pacman -Qe # e for manually installed

# Install
pacman -S `package`

# Remove
pacman -R `package`
pacman -Rns `package`
pacman -Rcns `package` # Uninstall with all the dependencies

# Query
pacman -Q `package`
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

# makepkg

- Build user package in Archlinux
- Requires package `base-devel`

```shell
git clone https://aur.archlinux.org/google-chrome.git
cd google-chrome/
makepkg -s # Creates pacman package
sudo pacman -U pacote.pkg.tar.xz # Install package

# Make and install
makepkg -si
```

```shell
makepkg --syncdeps --rmdeps --clean --install --cleanbuild
makepkg -srciC
```

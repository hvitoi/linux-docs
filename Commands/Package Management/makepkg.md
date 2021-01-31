# makepkg

- Build user package in Archlinux
- Requires package `base-devel`

```sh
git clone https://aur.archlinux.org/google-chrome.git
cd google-chrome/
makepkg -s # Creates pacman package
sudo pacman -U pacote.pkg.tar.xz # Install package

# Make and install
makepkg -si
```

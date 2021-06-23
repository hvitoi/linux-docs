# apt

- Advance Package Tool
- Repositories are stored at `/etc/apt/sources.list` and in the folder `/etc/apt/sources.list.d`

## Basic operations

```shell
# Install package
sudo apt install `package`

# Uninstall package
sudo apt remove `package`
sudo apt purge `package` # Removes all personal data as well

# Update source list
sudo apt update

# Upgrade all packages
sudo apt upgrade
sudo apt full-upgrade

#Remove unnecessary libs
sudo apt autoremove
```

## Package Info

```shell
# List all available packages
sudo apt list

# List installed packages
apt list
apt list --installed
apt list --upgradeable

# Search a package
apt search `package`

# Show info about a package
apt show `package`

# List manually installed packages
zcat /var/log/apt/history.log.*.gz | cat - /var/log/apt/history.log | grep -Po '^Commandline: apt install (?!.*--reinstall)\K.*'
```

## Advanced operations

```shell
# Edit source list
sudo apt edit-sources

#Fix broken installation
sudo apt install --fix-broken
sudo apt install -g

## Install .deb
sudo apt install `./package.deb`
```

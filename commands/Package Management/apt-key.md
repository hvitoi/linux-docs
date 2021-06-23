# apt-key

- `/etc/apt/trusted.gpg`
- `/etc/apt/trusted.gpg.d/`

```shell
# List all keys
sudo apt-key list

# Add key curl standard input
sudo apt-key add `key` # PGP public key
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
wget -qO - `url` | sudo apt-key add -

# Verify key
sudo apt-key fingerprint `0EBFCD88`

# Delete key
sudo apt-key del `keyid`
```

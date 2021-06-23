# gpg

- OpenPGP is a non-proprietary protocol for encrypting email communication using public key cryptography
- It is based on the original PGP (`Pretty Good Privacy`) software
- GnuPG, also known as GPG, is a command line tool with features for easy integration with other applications

```shell
gpg --keyserver-options auto-key-retrieve --verify `archlinux-version-x86_64.iso.sig`

curl -sS https://download.spotify.com/debian/pubkey_0D811D58.gpg | gpg --import -
```

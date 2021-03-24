# sudo

- SUDO - Super User DO

```bash
# Change into super user
sudo -s # Same as su -

# print sudoers configuration
sudo -ll
```

## visudo

- Command used to edit the `/etc/sudoers`
- visudo adds groups to `/etc/sudoers`
- By default members of the group sudo (or wheel) are allowed to execute any command

```bash
# visudo with vi
visudo

# visudo with vim
EDITOR=vim visudo
```

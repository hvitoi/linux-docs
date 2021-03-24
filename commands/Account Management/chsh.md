# chsh

- Change default shell
- The shell binary must be authorized in `/etc/shells`

```sh
# Change the default shell for the current user
chsh -s `shell`

# Example for zsh
chsh -s $(which zsh) # Log out to apply!

# Check the user shell
cat /etc/passwd | grep `username`
echo $SHELL
```

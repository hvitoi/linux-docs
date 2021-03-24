# usermod

- Change a user

```bash
# Add user to a group
usermod -G `group` `user` # The user is removed from all the other groups

# Add user to another group (append)
usermod -aG `group` `user`
usermod -aG sudo spiderman # Add spiderman to the group sudo, now it can sudo commands

# Remove user from group
gpasswd -d `user` `group`
```

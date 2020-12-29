# setfacl - Set File Access Controll List

- Access Control List (ACL) provides flexible permission mechanism
- It's an additional permission system
- Allows access for a user without having to add it to a group (g) or to allow access to "others" (o)

```bash
# Modify a file ACL
setfacl -m u:`user`:rwx `file` # Set rwx to a user
setfacl -m g:`group`:rwx `file` # Set rwx to a group

# Recursive mode in a directory
setfacl -Rm `entry` `directory`

# Remove a ACL entry from a user
setfacl -x u:`user` `file`

# Remove all ACL entries from everyone
setfacl -b `file`
```

- Files with ACL receives a `+` in the permissions listing (ls)
- Even with write permission, users cannot delete a file with ACL

# chown - Change ownership

- There are 2 owners of a filer or directory
  - User
  - Group

```bash
# Change user ownership
sudo chown `new-user-owner` `file`
sudo chown -R `new-user-owner` `folder` # Recursive

# Change user and group ownership
sudo chown `new-user`:`new-group` `file`
sudo chown hvitoi:root texto.txt
```

- Only root can change user and group ownership
- A file can be deleted even if the user has no permission to access it if the folder that contains it has the propper permissions

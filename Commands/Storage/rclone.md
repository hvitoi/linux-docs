# rclone

```sh
# Configure remote storage server
rclone config

# Get all remotes
rclone listremotes

# Get storage info about a remote
rclone about `remote`:`path`
rclone about hvitoi:/
```

## List

```sh
# Print files
rclone lsf `remote`:`path`

# Tree
rclone tree `remote`:`path`
```

## Copy

- It is always the contents of the directory that is synced, not the directory so when source:path is a directory, it's the contents of source:path that are copied, not the directory name and contents.

```sh
# Copy the content
rclone copy `/local/path` `remote`:`/remote/path`
rclone copy ~/Documents/my-folder hvitoi:/my-folder
```

## Sync

```sh
# dry-run
rclone sync --dry-run `/local/path` `remote`:`/remote/path` # "test" the sync, but do not perform data transfer

# interactive mode
rclone sync -i `/local/path` `remote`:`/remote/path` # prompt for decisions

# progress mode
rclone sync -P `/local/path` `remote`:`/remote/path` # real-time transfer statistics
```

## Mount

- Mount remote to a mount point

```sh
# mount
rclone mount `remote`:`/remote/path` `/local/path`
rclone mount hvitoi:/ /mnt/hvitoi
```

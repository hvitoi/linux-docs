# rsync

- Remote Synchronization
- Utility for transferring and synchronizing files within same computer or to a remote computer
- Compares the modification time and size of the files
- Rsync is a lot faster than ftp or scp
- Used mostly to `backup` files
- Port `22` (same as SSH)
- Rsync uses SSH to transfer the files!

```shell
# Install rsync
sudo apt install rsync
sudo yum install rsync
```

```shell
# Use rsync
rsync `options` `source` `destination`
rsync -zvh `/local-file-src` `/local/folder/dest` # Local file sync
rsync -azvh `/local/folder/src` `/local-folder-dest` # Local directory sync

rsync -avz `/local-file-src` `user@ip:/remote/folder/dest` # Push to remote server
rsync -avzh `user@ip:/remote-file-src` `/local/folder/dest` # Pull from remote server

# Local sync
tar -cvf backup.tar /home/hvitoi
mkdir /tmp/backups
rync -zvh /home/hvitoi/backup.tar /tmp/backups # sync the file in the home and backups dirs
rync -azvh /home/hvitoi/hvitoi /tmp/backups  # sync the folder

# Remote sync
mkdir /tmp/backups # folder on remote server
rync -avz /home/localfile hvitoi@192.168.1.30:/home/hvitoi/remote/folder # sync file to remote server
rync -avzh hvitoi@192.168.1.30:/home/hvitoi/serverfile /home/local/folder
```

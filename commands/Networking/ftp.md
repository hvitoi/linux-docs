# ftp

- File Transfer Protocol is a standard network protocol used for transfering files between client and server
- FTP port: `21`

## Configure server

```shell
# Install FTP server
sudo apt install vsftpd
```

- Config file for ftp server: `/etc/vsftpd.conf`

```conf
anonymous_enable=NO
ascii_upload_enable=YES
ascii_download_enable=YES
ftpd_banner=Welcome to blah FTP service.

# Local time
use_localtime=YES
```

- Start vsftpd service

```shell
systemctl start vsftpd
systemctl enable vsftpd
```

- Stop firewall service (only if necessary!)
- Instead of disabling the firewall, you must add rule to allow port 21 as incoming traffic

```shell
systemctl stop firewalld
systemctl status firewalld\
systemctl disable firewalld
```

## Configure client

```shell
# Install FTP client
sudo apt install ftp
```

- Start transation

```shell
# Open FTP console
ftp # 'bye' to exit

# Connect to a server
ftp `ip` # By default it picks the username of the user linux session!
ftp 192.168.1.58
```

- FTP console

```ftp
bin
hash
put file-name
bye
```

- `bin`: Switch to binary mode
- `hash`: Show progress bar
- `put`: Transfer a specific file
- `get`: get file from server

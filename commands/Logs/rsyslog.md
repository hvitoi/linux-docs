# rsyslog

- Generate logs or collect logs from other servers
- Acts like a central logger
- Configuration file: `/etc/rsyslog.conf`
- Port 514

```sh
# Install package/service
sudo apt install rsyslog

# Start service
systemctl status rsyslog
```

```conf
*.* @@127.0.0.1:10514
```

- `*.*`: Forward all messages
- `@`: transmit through UDP connections
- `@@`: transmit through TCP connections
- `127.0.0.1:10514`: where to send logs to

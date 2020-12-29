# chronyc

- Replacement for the ntp server
- Enhanced features
- Time synchronization
- Configuration file `/etc/chronyd.conf`
- Log file `/var/log/chrony`

```sh
# Install service
sudo apt install chrony

# Start service
systemctl start chronyd

# Interactive mode
chronyc
- sources # server to synchronize time
- quite # quit
```

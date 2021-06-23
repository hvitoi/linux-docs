# ntpq

- Network Time Protocol (NTP)
- Time synchronization
- Configuration file: `/etc/ntp.conf`
- Runs on port 123

```shell
# Check service daemon
systemctl statys ntpd
```

```shell
# NTPq interative mode
ntpq
- peers # Show servers connected to get the time
- quite # Quit
```

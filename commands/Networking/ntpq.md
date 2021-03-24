# ntpq

- Network Time Protocol (NTP)
- Time synchronization
- Configuration file: `/etc/ntp.conf`
- Runs on port 123

```sh
# Check service daemon
systemctl statys ntpd
```

```sh
# NTPq interative mode
ntpq
- peers # Show servers connected to get the time
- quite # Quit
```

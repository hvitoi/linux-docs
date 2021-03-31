# Log Monitoring

- All logs in Linux machine are stored at `/var/log`

```sh
cat "/var/log/boot.log" # Messages from the boot. Generated on every startup
cat "/var/log/auth.log" # Logging activity
cat "/var/log/messages" # All information and error messages from applications, processes and hardware. The most important log!
cat "/var/log/kern.log"
cat "/var/log/syslog"
```

```sh
# Follow logs
less +F "/var/log/syslog"
```

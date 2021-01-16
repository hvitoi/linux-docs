# dmesg

```bash
# System related warnings, error messages, failures
sudo dmesg
sudo dmesg | more
```

## Log Monitoring

- All logs in Linux machine are stored at `/var/log`

```bash
sudo cat /var/log/boot.log # Messages from the boot. Generated on every startup
sudo cat /var/log/auth.log # Logging activity
sudo cat /var/log/messages # All information and error messages from applications, processes and hardware. The most important log!
sudo cat /var/log/kern.log # ouitput from dmesg
sudo cat /var/log/syslog
```

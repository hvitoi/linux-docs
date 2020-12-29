# Fix volume delay issue

- At `/etc/pulse/daemon.conf`
- Uncomment `enable-deferred-volume` line and change value to `no`

```bash
pulseaudio -k && pulseaudio --start
```

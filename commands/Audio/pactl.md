# pactl

- Pulse Audio CTL

```sh
# List connections
pactl list
pactl list | grep -C2 A2DP

# List specific
pactl list cards
pactl list sources
pactl list sinks
pactl list modules
```

## Fix volume delay issue

- At `/etc/pulse/daemon.conf`
- Uncomment `enable-deferred-volume` line and change value to `no`

```bash
pulseaudio -k && pulseaudio --start
```

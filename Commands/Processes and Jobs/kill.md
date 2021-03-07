# kill

- Kills by the process id (pid)

```bash
# Kills a process
kill "pid" # Uses TERM signal by default

# Choose Signal
kill -9 "pid" # SIGTERM
```

## Signals

- Default signal is 15

```sh
#List signals
killall -l
```

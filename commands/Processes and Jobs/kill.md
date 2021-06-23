# kill

- Kills by the process id (pid)

```bash
# Kills a process
kill "pid"

# Choose Signal
kill -9 "pid" # SIGKILL
kill -s "signal" "pid" # SIGKILL
```

## Signals

- Default signal is 15 (SIGTERM)

```shell
#List signals
kill -l
```

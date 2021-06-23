# killall

- Similar to `kill`, but kill by process name

```bash
# Closes completely program
killall "process-name"
killall -9 "google-chrome-stable"

# Choose signal
killall -s 9 "process-name" # SIGKILL
killall -9 "process-name"

# Wait the process to terminate before closing
killall -w "process-name"
```

## Signals

- Default signal is 15 (SIGTERM)

```shell
#List signals
killall -l
```

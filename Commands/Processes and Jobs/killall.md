# killall

- Similar to `kill`, but kill by process name

```bash
# Closes completely program
killall "process-name"
killall -9 "google-chrome-stable"

# Choose signal
killall -s 9 "process-name"
killall -9 "process-name"
```

## Signals

- Default signal is 15

```sh
#List signals
killall -l
```

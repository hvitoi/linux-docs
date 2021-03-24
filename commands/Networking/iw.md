# iw

- Network manager using `ip` command

```sh
# Show interfaces
iw dev

# Scan wifi
iw dev `interface` scan | less

# Connect
iw dev `interface` connect `ssid`
```

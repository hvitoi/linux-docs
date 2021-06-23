# iw

- Network manager using `ip` command

```shell
# Show interfaces
iw dev

# Scan wifi
iw dev `interface` scan | less

# Connect
iw dev `interface` connect `ssid`
```

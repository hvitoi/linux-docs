# nmcli

- Installed with the package `networkmanager`
- First the service must be enabled `systemctl enable NetworkManager.service`

```shell
# Show all devices and its status
nmcli device
nmcli device status

# Show specific device
nmcli device show "wlp3s0"
```

```shell
# Show wifi networks
nmcli device wifi list

# Connect to wifi
nmcli device wifi connect "SSID_or_BSSID" password "password"

# Show password of current wifi
nmcli device wifi show-password
```

```shell
# Show all connections (wifi, bridge, vpn, ethernet)
nmcli connection
nmcli connection show

# Up a connection
nmcli connection up "connection-name"
```

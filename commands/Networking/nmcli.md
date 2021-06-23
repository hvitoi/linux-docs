# nmcli

- Installed with the package `networkmanager`
- First the service must be enabled `systemctl enable NetworkManager.service`

```shell
# Show wifi list
nmcli device wifi list

# Connect
nmcli device wifi connect `SSID_or_BSSID` password `password`
```

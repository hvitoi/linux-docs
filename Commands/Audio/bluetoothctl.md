# bluetoothctl

## List

```sh
# List controllers
bluetoothctl list

# List available devices
bluetoothctl devices

# Show info about a device
bluetoothctl info "mac-addr"
```

## Pairing

```sh
# List paired devices
bluetoothctl paired-devices

# Scan devices
bluetoothctl scan on

# Pair
bluetoothctl pair "mac-addr"

# Cancel pairing process
bluetoothctl cancel-pairing `mac-addr`

# Unpair
bluetoothctl remove `mac-addr`
```

## Connection

```sh
# Connect
bluetoothctl connect `mac-addr`

# Disconnect
bluetoothctl disconnect `mac-addr`


```

## Trust

```sh
# Trust
bluetoothctl trust `mac-add`

# Untrust
bluetoothctl untrust `mac-add`
```

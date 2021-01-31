# bluetoothctl

## List

```sh
# List controllers
bluetoothctl list

# List available devices
bluetoothctl devices

# Show info about a device
bluetoothctl info `mac-addr`
```

## Pairing

```sh
# List paired devices
bluetoothctl paired-devices

# Scan devices
bluetoothctl scan on

# Pair
bluetoothctl pair `mac-addr`

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

## Bluetooth pairing on Windows and Linux simultaneously

- Connect device on Linux and afterwards on Windows
- Boot Linux again

```sh
sudo apt install chntpw
cd /media/hvitoi/Windows/Windows/System32/config
chntpw -e SYSTEM
```

```powershell
# Navigate to bluetooth keys folder
cd CurrentControlSet\Services\BTHPORT\Parameters\Keys # if there is no CurrentControlSet, then try ControlSet001

# List bluetooth ports mac addresses
ls
cd aa1122334455

# Cd into the bluetooth device MAC
ls

# Show device connection key
hex 001f20eb4c9a # response like 00000 XX XX XX XX XX XX XX XX XX XX XX XX XX XX XX XX ...ignore..chars..
```

```sh
sudo -s
cd /var/lib/bluetooth/`port-mac`/`device-mac`
vim info # change to LinkKey to windows key

```

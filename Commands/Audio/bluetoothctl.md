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
cd 3413E8C296A0

# Show device connection key
ls
hex 001f20eb4c9a # response like 00000 XX XX XX XX XX XX XX XX XX XX XX XX XX XX XX XX ...ignore..chars..
```

```txt
Device 5C:C6:E9:A0:BB:15 EDIFIER W800BT
HEX F24E4C75A0A3F1CF18AF46D55E6AC043

Device 60:F4:3A:29:91:D0 EDIFIER R1080BT
HEX 2C593CC1A8683DB42A62BBDF78B9CA47

Device 5C:FB:7C:88:FA:49 JBL TUNE110BT
HEX F082CC36B73C800C7FBA9D2225BDAFE6
```

```sh
sudo -s
cd /var/lib/bluetooth/`port-mac`/`device-mac`
vim info # change to LinkKey to windows key
```

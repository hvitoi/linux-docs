# ethtool

- Get information about a specific NIC
- The NIC is showed in the `ip a` command

```sh
# Show info about the NIC
ethtool `nic`
ethtool enp0s3
```

## NIC information

- `Supported link modes`: 10baseT, 100baseT, 1000baseT
- `Speed`: 1000Mb/s
- `Duplex`: Full/Half
- `Link detected`: yes/no, up/down

## NIC bonding

- Aggregation or combination or multiple NIC into a single bond interface. It's a `network bonding`
- Provide high availability and redundancy (if one dies, the other can provide info)
- Example: bond NIC `enp0s3` and `enp0s8`

```sh
modprobe bonding # Add bonding module
modinfo bonding # Info about bonding module
```

- `/etc/sysconfig/network-scripts/ifcfg-bond0` (create)

```config
DEVICE=bond0
TYPE=Bond
NAME=bond0
BONDING_MASTER=yes
BOOTPROTO=none
ONBOOT=yes
IPADDR=192.168.1.80
NETMASK=255.255.255.0
GATEWAY=192.168.1.1
BONDING_OPTS="mode=5 miimon=100"
```

- The IPADDR will be the ip of the new interface, it should not be taken already

- `/etc/sysconfig/network-scripts/ifcfg-enp0s3` (edit)

```config
TYPE=Ethernet
BOOTPROTO=none
DEVICE=enp0s3
ONBOOT=yes
HWADDR=08:00:27:c3:0e:28
MASTER=bond0
SLAVE=yes
```

- `/etc/sysconfig/network-scripts/ifcfg-enp0s8` (edit)

```config
TYPE=Ethernet
BOOTPROTO=none
DEVICE=enp0s8
ONBOOT=yes
HWADDR=08:00:27:0d:17:9b
MASTER=bond0
SLAVE=yes
```

- Restart the network service

```sh
systemctl restart network
cat /proc/net/bonding/bond0 # Verify the bonding
```

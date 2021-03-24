# IP command

- Command `ip` is in `iproute2` package

```bash
## List all available ip addresses
ip address
ip addr
ip a

# Check network interfaces
ip link

# Set interface up
ip link set `interface` up
ip link set wlp3s0 up

# Interface status
ip link show `interface`

# List all available ip addresses (deprecated)
ifconfig
```

- `IP`: Identifies each computer using Internet Protocol
- `Subnetmask`: Masks the IP. Divide the IP into network address and host address
- `Gateway`: Which route to take to send the traffic out or to receive traffic
- `Static IP`: IP does not change for a machine
- `DHCP`: Takes the address from a pool of IPs and assign to a machine upon connection
- `Interface`: a NIC (Network Interface Controller) card. Ethernet, Wi-Fi, etc. Always have a MAC address that never changes (E.g, 3A-34-52-C4-69-B8)

## Interface configuration files

- `/etc/nsswitch.conf`
  - Tells the system where it should resolve some functionalities of the system (E.g, resolve the hostname to ip address -> hosts: files mdns4_minimal [NOTFOUND=return] dns)
- `/etc/hosts`: resolve hostname to ip address
- `/etc/hostname`: current hostname
- `/etc/network/interfaces`: Interfaces
- `/etc/resolv.conf`: IP to the DNS server! Resolve hostname-ip, ip-hostname, hostname-hostname
- `/etc/sysconfig/network-scripts/ifcfg-nic`: Static IP configuration

## Protocols or clients to access the system

- Windows: Remote Desktop RDP (for Windows)
- VMware ESC: vSphere client (for Windows)
- Linux: Putty (for Windows), SecureCRT, SSH from Linux to Linux

## NIC (Network Interface Card)

- `NICs` in `ip addr`

  - `lo`: Loopback device. Interface for the computer to communicate with itself
  - `virb0`: Virtual bridge is used for NAT (Network Address Translation )
  - `enp`: Cabled network
  - `wlp`: Wireless network

- enp2s0: Wired connection
- wlp3s0: Wireless connection

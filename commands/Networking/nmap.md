# nmap

- Network mapping tool
- It works by sending various network messages to the IP addresses in the subnet

```sh
# List of active IP addresses
sudo nmap -sn "192.168.1.0/24"

# Detailed summary
sudo nmap "192.168.1.0/24"

# Aggressive scan
sudo nmap -A -T4 "192.168.1.11"
```

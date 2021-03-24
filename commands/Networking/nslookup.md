# nslookup

- Requires package `dnsutils`

```sh
# Find the IP from a hostname
nslookup `hostname`
nslookup www.google.com

# Find the hostname of a ip
nslookup `ip`
nslookup 172.217.28.4
```

- `Server`: is the resolver. The DNS server. Usually the modem or the router
- `Address`: the ip and port of the DNS server
- `Non-authoritative answer`: Means that the DNS server (modem) does not have info about the provided hostname (E.g., www.google.com), therefore it went outside on the internet to find that info
- The DNS server does already have the info about the hostname saved in the local environment. It's NOT shown as non-authoritative answer

## DNS

- Domain Name System (DNS)
- DNS is a system to translate a `hostname` to `ip address` and vice-versa
- `8.8.8.8` google DNS server configured to provide DNS resolutions

- Translation types

  - `A Record`: hostname to ip (forward)
  - `PTR Record`: ip to hostname (reverse)
  - `CNAME Record`: hostname to hostname

- DNS setup

  - Master DNS
  - Secondary or slave DNS
  - Client

- `bind9` is the name of the DNS package

```sh
sudo apt install bind9
apt-get install bind9-doc
```

- `named` is the name of the dns service

```sh
systemctl status named
```

- DNS configuration files

  - `/etc/bind/named.conf`
  - `/etc/bind/named.conf.options`
  - `/etc/bind/named.conf.local`
  - `/etc/bind/named.conf.default-zones`

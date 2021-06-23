# telnet

- Old and unsecured connection between computers
- Similar to ssh!
- `telnet` package must be installed. It does not come on linux out of the box
  - `sudo apt install telnet`

```shell
# Telnet an IP and port
telnet `ip` `port`
telnet mywebsite.com 443

# Set escape character
echo X | telnet -e X localhost 3306 # MySQL connection
```

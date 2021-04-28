# ss

- Monitor Network Connections

```sh
# List all connection (regardless of the state)
ss

# Both listening and non-listening ports
ss -a

# Listening sockets
ss -l

# TCP connections
ss -t
ss -tl # tcp listening ports

# UDP connections
ss -u
ss -ul

# Display PID of sockets
ss -p

# Summary
ss -s

```

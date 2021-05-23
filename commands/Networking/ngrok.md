# ngrok

- Expose your localhost
- It's reverse proxy
- Creates a secure tunnel of a public endpoint to a service running in your machine
- Web UI to inspect the requests: <http://localhost:4040>

## Login

```shell
# Login
ngrok authtoken "token"
```

## HTTP services

```shell
# Expose HTTP service
ngrok http "3000" # generates a random URL

# Expose HTTP service with basic auth
ngrok http -auth "username:password" "3000"
```

## TCP services

```shell
# Expose SSH service
ngrok tcp "22"

# Expose Postgres service
ngrok tcp "5432"
```

## Filesystem

```shell
# Expose your filesystem
ngrok http "file:///home/hvitoi/Downloads"
```

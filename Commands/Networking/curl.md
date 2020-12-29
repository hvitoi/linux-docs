# Curl

- Similar to `wget`
- Mostly used for REST request

```bash
## Fetch the content of the URL and display immediately
curl `url`
curl www.google.com

## Save the page to a file
curl `url` -o `out-file`
curl www.google.com -o ./google.html

## Save file directly with original file
curl -O `url`
curl -O http://mirror.bytemark.co.uk/ubuntu-releases/18.04.4/ubuntu-18.04.4-desktop-amd64.iso

## Redirecting pages. The http page is redirecting to the https page, so nothing is displayed!
curl -l `url` # -l saves the redirected page
curl -l http://hsploit.com/

## Querying response
curl -I `url`

## TLS handshake - Additional information regarding the connection
curl -v `url`

## Test credentials - HTTP POST data
curl --data "key1=value1&key2=value2" `url`
curl --data "log=admin&pwd=password" https://wordpress.com/wp.login.php

# Do not show the progress bar
curl -s `url`

# Curl and pipe to bash
curl -sL https://deb.nodesource.com/setup_14.x | bash -
sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose # L for location


# Add headers to the request
 curl -H "key:value" `url`
```

## Script for testing requests

```bash
while true;
do curl -s fleetman.dev:31380/ | grep title;
  sleep 0.5;
done;
```

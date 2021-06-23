# dpkg-query

- QUery packages installed

```shell
# List all non-free packages
dpkg-query -W -f='${Section}\t${Package}\n' | grep ^non-free

# List packages
dpkg-query --list
```

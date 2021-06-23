# less

- View the content one line at a time
- `Shift+F` goes to the bottom of the file

```shell
# Read text file line by line (q quits)
less `filename`

# Pipe
ls -l | less

# Follow logs
less +F "/var/log/syslog"
```

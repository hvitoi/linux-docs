# journalctl

- Storage place: `/var/log/journal`
- Journal config: `/etc/systemd/journald.conf`

## Log severity

| Value |   Severity    | Keyword |                           Description                           |
| :---: | :-----------: | :-----: | :-------------------------------------------------------------: |
|   0   |   Emergency   |  emerg  |                       System is unusable                        |
|   1   |     Alert     |  alert  |                 Should be corrected immediately                 |
|   2   |   Critical    |  crit   |                       Critical conditions                       |
|   3   |     Error     |   err   |                        Error conditions                         |
|   4   |    Warning    | warning |  May indicate that an error will occur if action is not taken.  |
|   5   |    Notice     | notice  |       Events that are unusual, but not error conditions.        |
|   6   | Informational |  info   |       Normal operational messages that require no action.       |
|   7   |     Debug     |  debug  | Information useful to developers for debugging the application. |

## Journal

```shell
# Boot messages
journalctl -b # current boot
journalctl -b -1 # last boot
journalctl --list-boots # list boot numbers

# By time
journalctl --since="2012-10-30 18:17:16"
journalctl --since "20 min ago"

# Follow new messages
journalctl -f

# By application
journalctl /usr/lib/systemd/systemd
journalctl _PID=1
journalctl -u man-db.service

# Log severity
journalctl -p err..alert # only error, critical and alert (not emerg (0))
journalctl -p 1..3 # 3, 2, 1
journalctl -p 3 # 3, 2, 1 and 0

# Jump to the end
journalctl -e

# Add message explanations where available
journalctl -x

```

# crontab

- Schedule processes (cronjobs)
- Processes scheduled by crontab can be hourly, daily, weekly, monthly, etc...

```bash
# Schedule a cronjob
crontab -e # Edit the list of cronjobs in vi

# Subtitute all entries in crontab
echo "* * * * * root echo 'oi' > /root/oi" | crontab -

# Add entry to crontab
(crontab -l && echo "* *  * * *  test") | crontab -

# List all cronjobs
crontab -l
```

- Cronjob example

```vi
22 13 * 3 * echo "Bom dia!" > ~/Downloads/lol.txt
```

- <https://crontab.guru/every-10-minutes>

- `Minute`: 22
- `Hour`: 13
- `Day of the month` \* (everyday)
- `Month`: 3 (march)
- `Week`: \* (every week)
- `Command`: echo "Bom dia!" > ~/Downloads/lol.txt

## Cron directories

- Each folder contain **scripts** that will run at a point in time according to the folder name

```bash
# list cron folders
ls -la /etc | grep cron.
ls -la /etc/cron.* # List the content of each one
```

- /etc/crontab: Store the crontabs created with `crontab -e`
- /etc/cron.d
- /etc/cron.hourly
- /etc/cron.daily
- /etc/cron.weekly
- /etc/cron.monthly

- The `/etc/anacrontab` store the configuration about the `daily`, `weekly` and `monthly` jobs
- The `/etc/cron.d/0hourly` stores the configuration about the `hourly` job

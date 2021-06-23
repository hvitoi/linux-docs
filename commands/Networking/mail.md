# sendmail

- Configuration files:
  - `/etc/mail/sendmail.mc`
  - `/etc/mail/sendmail.cf`: Created by the mc file
- All the configs are stored at `/etc/mail`

```shell
sudo apt install sendmail
sudo apt install sendmail-cf # Configration package
```

```shell
systemctl status sendmail
```

```shell
# Send email
mail -s `subject` `mail-address`
mail -s "My email" mail@gmail.com # Opens interactive mode to write body. Ctrl + D to finish
```

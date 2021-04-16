# chntpw

- Mount Windows
- At `/media/hvitoi/Windows/Windows/System32/config`

```sh
# Regedit
chntpw -e SYSTEM

# Check user records in Security Account Manager (SAM)
chntpw -l SAM # list
chntpw -i SAM # edit

```

# useradd

```bash
useradd `user` # If no group is specified, it's added to a group with the same name

useradd \
  -g `group` \
  -s `/bin/bash` \
  -c `description` \
  -d /home/user \
  -m \
  `user`
# g - add user to a group
# s - shell
# c - description
# d - home directory
# m - create the home directory

useradd \
  -rm \
  -d /home/ubuntu \
  -s /bin/bash \
  -g root \
  -G sudo \
  -u 1000 \
  hvitoi
```

- The list of users can be seen in `/etc/passwd`
- In order to login as a user a password must be defined with `passwd`

## Linux Account Authentication

- **Types of accounts**

  - Local account
  - Domain/Directory account

- **Directory Service**

  - _Microsoft_
    - Directory service:`Active Directory`
    - Login protocol: `LDAP`
  - _RHEL_
    - Directory Service: `IDM` (Identity Manager)
  - _IBM_
    - IBM Directory Server
  - _Cloud_
    - JumpCloud

- **Login Protocols** (used to authenticate against a directory)
  - `LDAP` (Lightweight Directory Access Protocol): Used mostly on Windows
  - `WinBIND`: Windows users (AD) access their account in Linux machines (SAMBA)
  - `OpenLDAP` - Open authentication protocol: Used mostly on Linux. `slapd` service

### OpenLDAP server

- Service for configuring the OpenLDAP server: `slapd`
- Configuration folder `/etc/openldap/slapd.d/`
- `/etc/nsswitch.conf` shows the options to choose for account management
  - Checks the field `passwd: files sss`
  - `sss` is the ldap server, it's the second option after a user is not found locally

```shell
# Install
sudo apt install *openldap*

# Service
systemctl status slapd
ps -ef | grep slapd
```

# Virtualbox networking

## Configure VM as a VM

```bash
sudo apt update
sudo apt install build-essential module-assistant dkms
sudo m-a prepare
--> `Insert VirtualBox Guest Additions ISO here`
sudo -s
sh /media/cdrom/VBoxLinuxAdditions.run
sudo adduser pi vboxsf # Allows folder sharing
```

## Add shared folder

- Devices / Shared Folder
- Make permanent
- Auto Mount
- Mount point /home/hvitoi/Documents

## SSH connection

- Bridge mode
- `ip a` get ip address

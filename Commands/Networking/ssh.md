# ssh

- Secure connection between computers

## SSH server

- In a VM, the bridge mode must be enabled to use SSH
- `/etc/ssh/sshd_config`: Configuration file for a ssh server
- `~/.ssh/authorized_keys/`: Stores public keys of the allowed clients

### Install server

```sh
# Install ssh-server
sudo apt install openssh-server

# Check ssh service
sudo systemctl status ssh
ps -ef | grep sshd # /usr/sbin/sshd

# Get ip of the machine
ip addr # enp0s3 (192.168.0.109)

# Test connection to itself
ssh localhost
```

### Install public keys of the clients

- Keys in the server are stored at `~/.ssh/authorized_keys`

```sh
# Run these commands in the client side!
ssh-copy-id -i `/path/to/key.pub` `user`@`hostname`
ssh-copy-id -i ~/.ssh/id_ed25519.pub root@ip
```

## SSH client

- Keys are generated at user level (`~/.ssh`)
- `id_rsa`: secret file and never share
- `id_rsa.pub`: share with github, heroku, etc

### Generate keys

```sh
# List existing keys
ls ~/.ssh

# SSH key-pair generation
ssh-keygen # No options
ssh-keygen -t `rsa` -b `4096` -C `hvitoi@gmail.com` # type RSA
ssh-keygen -t `ed25519` -C `My ssh key for the Jenkins` # type ED25519
ssh-keygen -f `key-name` -m `PEM`  # Specify the name for the key (and create in the current directory)
# -t (type): rsa protocol
# -b (bits): bits fr the key
# -C: label/comment
# -f: output key file name
# -m: key format
```

### Add keys to client

```sh
# Start the ssh-agent in background (and print the process id)
eval "$(ssh-agent -s)"

# Add to the local computer
ssh-add -K `/path/to/key`
ssh-add -K ~/.ssh/id_rsa # -K (key): specify the file



```

### Connect to server via SSH

```sh
# Test connection
ssh -T `git@github.com` # Accept 'yes'

# Conventional ssh
ssh `user`@`hostname`
ssh root@192.168.1.10

# Specify user
ssh 192.168.1.10 -l root

# Specify port
ssh root@localhost -p 9090

# Specify key
ssh root@localhost -i private-sshkey
```

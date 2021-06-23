# yum

- Yum administrates the rpm packages
- yum downloads `rpm` files from repositories
- Repositories are stored at: `/etc/yum.repos.d`
- `rpm`: Red hat package Manager is the extension file for the binaries
  - rpm is used when you have already a package downloaded

```shell
# Install package
yum install `package`
yum install ksh* # Install everything with ksh keyword

# Uninstall package
yum remove `package`

# Upgrade packages: Install newer version and delete old packages. No rollback allowed!
yum upgrade -y # -y do not prompt for confirm

# Update packages: Install newer version and preserve the old ones. Rollback allowed!
yum update -y

# Clear cache
yum clean all

# List all repos
yum list all

# Yum commands history
yum history

# Undo a specific yum command
yum history undo `id` # If a update command is undone, the package will be downgraded
```

## Local repository

- Repository from DVD are used for environments without internet access
- First remove all the repo list from `/etc/yum.repos.d/`
- `/media/hvitoi/CentOS 7 x86_64/Packages`: CentOS rpm packages from official dvd.

  - Copy all these packages to any folder e.g. `/localrepo`

- Create a new local repo `local.repo` in `/etc/yum.repos.d/`

```txt
[centos7]
name=centos7
baseurl=file:///localrepo/
enabled=1
gpgcheck=0
```

- Create repo

```shell
# Create the repo containing the rpm packages locally
createrepo /localrepo

# Clear cache from the old repository
yum clean all

# List all repos
yum list all
```

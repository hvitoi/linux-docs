# rpm

- Package manager for red hat linux distributions

## Package information

```sh
# List all packages
rpm -qa

# Number of packages installed
rpm -qa | wc -l

# Check a specific package
rpm -qa | grep `package-name`

# Show package information
rpm -qi `package-name` # E.g., ksh-20120801-137.e17.x86_64

# Show package configuration
rpm -qc `package-name`

# Show the package that a command belongs to
rpm -qf `command-dir`
rpm -qf /etc/bin/ksh
```

## Install/Uninstall packages

```sh
# Install rpm package from file
rpm -ihv `/package/location.rmp`

# Uninstall a package
rpm -e `package-name` # E.g., ksh-20120801-137.e17.x86_64
```

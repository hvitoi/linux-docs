# lsb_release

- Check the OS release

```bash
lsb_release -a # verbose
lsb_release -d # simple
```

- `cat /etc/debian_version` for Debian-based distros
- `cat /etc/redhat-release` for Redhat-based distros

## Versioning

- Major version: 5, 6, 7
  - Cannot upgrade via `yum` or `apt`!
- Minor version: 7.3, 7.4
  - Can upgrade via `yum` or `apt`

# Locate

- Locate is faster because it uses a prebuilt database, which should be regularly updated
- Locate can be inaccurate if the database is not up to date

## Search files and directories

```bash
# Search Uses a prebuilt database (must be regularly updated) (Fast)
locate `file/dir`
```

```bash
# Update the db
sudo updatedb

# Required package
sudo apt install mlocate
```

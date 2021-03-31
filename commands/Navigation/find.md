# Find

- Find uses the 'hard way'. It iterates over the filesystem
- `find` searches files or directories iterating over the filesystem (Slow)

## Search files and directories

```bash
# Search and file name

find `location` -name `file/dir`
find / -name "sources.list"
find . -name "notes.txt"

# Search by file type and file name
file / -type f # f for file
file / -type d # d for directory

# REgex
find / -regex ".*\(bluez5\|bluetooth\).*\.so" -exec cp {} {}.bak \;
```

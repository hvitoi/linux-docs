# truncate

- Chop a file to a specified size

```bash
# Example file with 15 bytes
truncate -s 10 `file` # Truncate file to 10 bytes. Data is lost
truncate -s 20 `file` # Extends the file with @^@^ information untill 20 bytes
```

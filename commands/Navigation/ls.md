# ls - List

- `ls` is used for navigation through the `Linux File System`
- `Linux File System` uses the `File Hierarchy Standard` (FHS) structure
- `Linux File System` examples: EXT3, EXT4, XFS

## Shell

- GNU BASH (Bourne-Again SHell) vs. GUI (Graphical User Interface)

## File attributes

- `d`: Directory
- `l`: Link
- `-`: File
- `c`: Special file / Device file (cpu, keyboard, memory ... )
- `s`: socket (ex: /dev/sda)
- `p`: Named pipe
- `b`: Block device

## Listing info in `ls -la`

| `type`     | `links` | `owner` | `group` | `size` | `month` | `day` | `time` | `name`     |
| ---------- | ------- | ------- | ------- | ------ | ------- | ----- | ------ | ---------- |
| drwxrwxrwx | 1       | hvitoi  | root    | 4096   | mar     | 22    | 2:52   | Javascript |

## Listing

```bash
ls
ls -l
ls -la
ls -laF
ls -ltr # Time reverse order
ls -al / > lsout.txt # List the root dir and saves in the text file
ls -la /etc/cron.* # List the content of each folder starting with cron.
```

## Listing with wildcards

- Zero or more chars
  - `*` - `ls abc*`
- A single char
  - `?` - `ls ?bc*`
- Pick of characters
  - `[]` - `ls *[aeiou]*` # Either a, e, i, o, u
- Range of chars
  - `{}` - `touch abc{1..9}-xyz`
- Escape character
  - `\`
- Beginning of line
  - `^` - `ls -l | grep ^d` # List directories
- End of line
  - `$`

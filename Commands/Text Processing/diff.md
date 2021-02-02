# diff

- File comparison

```bash
# Returns the lines that differ between the two files. Shows also the line number
diff `file1` `file2`

# Compare folders
diff -bur `folder1/` `folder2/`
```

- `b` flag means ignoring whitespace
- `u` flag means a unified context (3 lines before and after)
- `r` flag means recursive

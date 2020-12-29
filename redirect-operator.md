# Redirect operator

- `> file` redirects stdout to file
- `1> file` redirects stdout to file
- `2> file` redirects stderr to file
- `&> file` redirects stdout and stderr to file
- `> file 2>&1` redirects stdout and stderr to file (deprecated)

```sh
# Show exit code from previous command
echo $?
```

```sh
# Send exit code to 2>/dev/null
# If there is error (||) return exit code success. (|) would always return success
cp ./a ./b 2>/dev/null || :
```

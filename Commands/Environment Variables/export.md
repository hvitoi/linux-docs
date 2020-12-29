# export

```bash
# Export an environment variable to the current environment
export MYVAR=value

# Print the environment variable
echo $MYVAR


# View all exported variables
export -p
```

## Useful environment variables

- `$HOSTNAME`: hostname
- `$TERM`: terminal used
- `$SHELL`: user shell
- `$0`: current shell
- `$HISTSIZE`: command history length
- `$USER`: current user
- `$PATH`: list of directories (separated by `:`) to search for commands when typed in the terminal.
- `$PWD`: current directory
- `$LANG`: system language configuration
- `$HOME`: home directory

## User environments

- `~/.bashrc`
- `~/.bash_profile`

- source `file` to apply right away

## Global environments

- `/etc/profile`
- `/etc/bashrc`
- `/etc/profile.d/`: preferred folder for global variables

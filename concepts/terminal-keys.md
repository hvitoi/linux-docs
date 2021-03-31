# Terminal Control keys

- `CTRL+C`: Stops/kills command
- `CTRL+Z`: Suspends a command
- `CTRL+D`: Exit from interactive program (signals end of data)
- `CTRL+L`: Clears the screen

## Cut text (kill/yank)

- `CTRL+K`: Cuts the text from the cursor until the end of line
- `CTRL+U`: Cuts the text from the cursor until the beggining of line
- `CTRL+W`: Cuts the previous word

- `CTRL+Y`: Paste back cut text

## Multiline terminal

- `CTRL+x+e`
- `wq!` to execute

```sh
for host in $HOSTS
do
  echo "${host}"
done
```

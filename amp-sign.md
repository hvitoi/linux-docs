# Amp sign

```sh
for i in `seq 1 10`; do curl http://site.com &; done
```

- This will print messages from the subscript, but you can replace the `&` with `>/dev/null &` and suppress the output.
a
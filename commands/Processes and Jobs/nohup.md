# nohup

- Similar to bg
- Send a process to the background

```bash
nohup `process` & # Creates a file nohup.out and logs there everything
nohup `process` > /dev/null 2>&1 &  # Shows no junk message
```

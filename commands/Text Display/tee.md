# tee

- Store and view at same time

```bash
# Tee (Displays and saves)
echo "Texto exemplo" | tee texto.txt # Replaces text (>)
echo "Texto exemplo" | tee -a texto.txt # Appends text (>>)

# Tee to multiple files
echo "Texto exemplo" | tee file1.txt file2.txt file3.txt
```

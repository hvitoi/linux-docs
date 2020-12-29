# grep

- Global regular expression print
- Print lines that match a specified pattern

```bash
# Create sample file
echo "Henrique Abrantes Vitoi
Lais Abrantes Vitoi
Simone Gomes Abrantes Vitoi
Luiz Henrique Rossi Vitoi" > family
```

```bash
# General usage
grep `keyword` `file`

# Parameters
grep -c `keyword` `file` # Count matching lines
grep -n `keyword` `file` # Display matching lines and show its number
grep -i `keyword` `file` # Case insensitive
grep -v `keyword` `file` # Intersection. Exclude the line that do not contain the keyword
grep -w `keyword` `file` # Match only whole words

# Pipe
ls -l ~/ | grep Desktop
```

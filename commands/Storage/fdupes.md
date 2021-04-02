# fdupes

- Find duplicate files

```sh
# Current folder
fdupe .

# Recursively with size and time info
fdupes --recurse . --size --time # -r . -S -t

# Order
fdupes --recurse . --order "time" --inverse # -r . -o "time" -i

# Delete duplicates (prompt)
fdupes --recurse . --delete # -r . -d

# Delete duplicates (no prompt)
fdupes --recurse . --delete --noprompt # -r . -d -N
```

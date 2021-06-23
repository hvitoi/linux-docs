# awk

- Text processing
- Mostly to get columns

```bash
# Create sample file
echo "Henrique Abrantes Vitoi
Lais Abrantes Vitoi
Simone Gomes Abrantes Vitoi
Luiz Henrique Rossi Vitoi" > family
```

```bash
# Print a column
awk '{print $1}' `file` # First column
awk '{print $1, $2}' `file` # First and second columns
awk '{print $NF}' `file` # Last column

# From pipe
ls -l | awk '{print $1, $NF}'

# Print lines
awk '/Henrique/ {print}' `file` # Print lines that have "Henrique"

# Modify the delimeter
awk -F ":" '{print $1}' `file` # Print the first column delimited by ":"
awk -F "/" '{print $1}' `file` # ...

# Replace words
echo "Hello Henrique" | awk '{$2="Henry"; print $0}' # Replace the second ($2) and print everything ($0)
awk '{$NF="Maluco"; print $0}' family

# Filter by length
awk 'length($0) > 25' `file` # Print only lines with more than 25 chars
awk 'length($0) > 25' family

# Filter by exact value
awk '{if($NF == "Vitoi") print $0;}' family

# Number of columns
ls -l | awk '{print NF}'
```

```shell
NAMESPACES=(desenvolvimento esteira-01 esteira-02 preproducao prodlike)
SERVICES=(disponibilidade landing-page product-catalog-fixa cart-fixa leads content)
for s in "${SERVICES[@]}"
do
  echo $s;
  for n in "${NAMESPACES[@]}"
  do
    POD=`kubectl get pod -n "$n" | grep "$s" | awk '{ print $1 }' | head -n "1"`
    echo "\t$n:" `kubectl get pod -n "$n" $POD -o "json" | jq ".spec.containers[0].image" | awk -F "\"" '{print $2}' | awk -F "/" '{print $2}' | awk -F ":" '{print $2}'`
  done
  echo "\n";
done
```

# egrep

- A grep with multiple keywords

```shell
# Create sample file
echo "Henrique Abrantes Vitoi
Lais Abrantes Vitoi
Simone Gomes Abrantes Vitoi
Luiz Henrique Rossi Vitoi" > family
```

```shell
# OR operator
egrep -i "keyword1|keyword2" "file" # Either the key1 or key2
egrep -i "Henrique|Vitoi" "family"
dmesg | egrep -i 'blue|firm'
```

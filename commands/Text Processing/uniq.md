# uniq

- Uniq identifies duplicates
- It's important to always sort first!

```bash
sort `file` | uniq # Returns only unique lines (Remote duplicates)
sort `file` | uniq -c # Display the unique lines and the number of occurrences
sort `file` | uniq -d # Shows only repeated lines
```

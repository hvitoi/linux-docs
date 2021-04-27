# pdftk

```sh
# Pick pages
pdftk "in.pdf" \
  cat 1-20 \
  output "out.pdf"

  # Pick pages
pdftk "in.pdf" \
  cat 21-end \
  output "out.pdf"
```

# latexdiff

- Diff between two versions of latex files
- `git-latexdiff` is a wrapper around latexdiff and diff
  - Allows diffing between two commits

```sh
# Diff between the last commit and the workspace
git latexdiff "HEAD~1" "--" \
  --main "main.tex" \
  --lualatex \
  --bibtex \
  --ignore-latex-errors \
  --type "UNDERLINE" \
  --output "/home/hvitoi/Downloads/diff.pdf"
```

- Markup styles
  1. UNDERLINE (default)
  1. CTRADITIONAL
  1. TRADITIONAL
  1. CFONT
  1. FONTSTRIKE
  1. INVISIBLE
  1. CHANGEBAR
  1. CCHANGEBAR
  1. CULINECHBAR
  1. CFONTCHBAR
  1. BOLD
  1. PDFCOMMENT

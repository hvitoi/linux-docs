# sed

- Replace string with a newstring
- Find and delete line
- Remove empty lines
- Replace tabs with spaces

```bash
# s - substitute
# g - global (entire file)
sed 's/word/newword/g' `file` # Substitute but does not save
sed 's/word//g' `file` # Substitute with nothing
sed 's/\t/ /g' `file` # substitute tab "/t" with spaces " "
sed -i 's/word/newword/g' `file` # Substitute and save

# d - delete
sed '/word/d' `file` # Delete the line with the word
sed '/^$/d' `file` # Delete empty lines. ^ anything that starts. $ anything that ends. In the middle there is nothing, so empty line
sed '1d' `file` # Delete line 1
sed '1,2d' `file` # Delete lines 1 and 2

# View lines
sed -n 12,18p `file` # view lines 12 to 18 # 'p' for pick
sed 12,18d `file` # view lines but 12 to 18 # 'd' for delete

# Add empty between lines
sed G `file`

# Substitute only certain occurrence
sed '8!s/word/S' `file` # SUbstitute all but the line 8
```

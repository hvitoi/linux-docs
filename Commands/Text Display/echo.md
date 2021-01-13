# echo

```bash
# Prints a text
echo "hey"

# Don't add line breaks
echo -n "Hey, there" # ends with a % (identify that it doesn't have a line break at the end)

# Enable interpretation of backslash escapes
echo -e "Hey, there\0"

# Add Text to Files
echo "This text replaces everything" > text.txt
echo "This text is appended" >> text.txt

# Add commands to echo
echo "The current date is $(date)."

# Output of a command into a text file
ls -l > text.txt
```

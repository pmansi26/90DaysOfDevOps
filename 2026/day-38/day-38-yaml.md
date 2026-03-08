# When to use | vs > in YAML

## 1. | (Literal Block Style)
- Used when you want to keep line breaks exactly as they are.
- Each line will remain on a new line.
- Commonly used for shell scripts, commands, or configuration blocks.
``` bash
Example:

script: |
  echo "Hello"
  echo "World"

Output:

echo "Hello"
echo "World"
```
## 2. > (Folded Block Style)
- Used when you want YAML to convert line breaks into spaces.
- The text becomes one single logical line.
- Commonly used for long messages, descriptions, or documentation text.
``` bash
Example:

message: >
  This is a long message
  written in multiple lines
  but it becomes one line.

Output:

This is a long message written in multiple lines but it becomes one line.
```
# Task 6: Spot the Difference
Block 2 is not broken, but it is poorly formatted and not recommended.
- docker starts at the same level as tools:
- YAML still interprets it as a list under tools
- But the formatting looks confusing and inconsistent

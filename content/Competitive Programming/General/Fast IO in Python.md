Because normal input/output is too slow.
```python
# Import the sys module to use stdin/stdout

import sys
sys.stdin = open("file.in", "r")
sys.stdout = open("file.out", "w")

# now you can use input() and print()
```

[StackOverflow source](https://stackoverflow.com/questions/11241523/why-does-python-code-run-faster-in-a-function)

This code
```python
def main():
    for i in xrange(10**8):
        pass
main()
```
runs faster than this code
```python
for i in xrange(10**8):
    pass
```
because python code runs faster when placed in a function.
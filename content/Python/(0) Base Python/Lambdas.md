- A small anonymous function.
- It can take any number of arguments, but can only have one expression.
- They are powerful when used inside other functions

## Syntax
```python
lambda arguments : expression
```

## Examples

### Basic
```python
x = lambda a : a + 10  
print(x(5))
```

### Multiple Arguments
```python
x = lambda a, b : a * b  
print(x(5, 6))
```

### Inside another function
```python
def myfunc(n):  
  return lambda a : a * n  
  
mydoubler = myfunc(2)  
mytripler = myfunc(3)
  
print(mydoubler(11))
print(mytripler(11))
```

*Use lambda functions when an anonymous function is required for a short period of time.*
- These allow you to quickly make new lists based on the values of an existing list.

# Example:
- Based on a list of fruits, you want a new list, containing only the fruits with the letter "a" in the name.

### Without list comprehensions:
```python

fruits = ["apple", "banana", "cherry", "kiwi", "mango"]  
newlist = []  
  
for x in fruits:  
  if "a" in x:  
    newlist.append(x)  
  
print(newlist)
```
This is slow.

### With list comprehensions:
```python
fruits = ["apple", "banana", "cherry", "kiwi", "mango"]  
  
newlist = [x for x in fruits if "a" in x]  
  
print(newlist)
```
This is just one line of code

## The syntax of any list comprehension
```python
newlist = [expression for item in iterable if condition == True]
```

### Expression
- The current item in the iteration
- This is what ends up added to the list, so you can do things like
```python
newlist = [x.upper() for x in fruits]
```
if you want.

### Condition
This is like a filter that only accepts the items that evaluate to `True`. 
- Example conditions:
	- `x != "apple"`
	- `x == 5`
	- etc…

### Iterable
- Any iterable object – a list, tuple, set, etc.
- A series is like a column in a table
- If nothing else is specified, the values in the series are labeled with their index number. First value has index 0, second value has index 1 etc.

Basic syntax to make a Series:
`s = pd.Series(data, index=index)`


```python
import pandas as pd  
  
a = [1, 7, 2]  
  
myvar = pd.Series(a)  
  
print(myvar)

'''
returns items with indexes (called labels):
0    1
1    7
2    2

'''
#0, 1, and 2 are labels, while 1, 7, and 2 are items.

print(myvar[0])
#returns 1
```

- With the *index* argument you can make custom labels.

```python
import pandas as pd  

a = [1, 7, 2]  
  
myvar = pd.Series(a, index = ["x", "y", "z"])  
  
print(myvar)

'''
returns:
x    1
y    7
z    2
'''

print(myvar["y"])
#returns 7
```

- You can also make a series from a *dict*
```python
import pandas as pd  

calories = {"day1": 420, "day2": 380, "day3": 390}  
  
myvar = pd.Series(calories)  
  
print(myvar)
#keep in mind that the keys of the dictionary become the labels. So the output is:

'''
day1    420
day2    380
day3    390
'''
```

- If there’s a missing data marker (as in, an index value that doesn’t return a data value), the result will be NaN.
![[Other/Images, Other Attachments/Pasted image 20230524190753.png]]
- You can also make a dataframe from scalar values:
![[Other/Images, Other Attachments/Pasted image 20230524191239.png]]
- [[https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.html#pandas.Series "pandas.Series"]] acts very similarly to a `ndarray` and is a valid argument to most NumPy functions. 
- However, operations such as slicing will also slice the index.

## How would some actual Series be made?
1. Creating a `Series` by passing a list of values. In this case since no index is specified Pandas creates a default index for us
![[Other/Images, Other Attachments/Pasted image 20230524191644.png]]
- Arrays are the central data structure of NumPy.
>  *An array is a grid of values and it contains information about the raw data, how to locate an element, and how to interpret an element. It has a grid of elements that can be indexed in [[https://numpy.org/doc/stable/user/quickstart.html#quickstart-indexing-slicing-and-iterating]]. Elements all have the same type.*
- Arrays have a `dtype` (the datatype of the elements), a `shape` (a tuple giving the size of the array along each dimension), and a `rank` (the number of dimensions)
- They are faster than Python lists

## Basic Examples
- Making an array from a python list
	- `a = np.array([1, 2, 3, 4, 5, 6])`
	- `a = np.array([[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]])`

## More Info about Arrays
- An array can also be referred to as a “ndarray,” which is shorthand for “N-dimensional array.”
- **Vector** - an array with 1 dimension
- **Matrix** - an array with 2 dimensions
- **Tensor** - an array with 3 or more dimensions
### Attributes of an array
- Each array has dimensions called *axes*.
- For example: this array has two axes. The first has a length of 2 and the second has a length of 3. 
```python
[[0., 0., 0.],
[1., 1., 1.]]
```
## Making basic arrays
- To make a NumPy array, use the function `np.array()`
- All that’s needed to do to make a simple array is to pass a list to it
```python
import numpy as np
a = np.array([1, 2, 3])
```
*In this case, here’s what’s happening:*
![../_images/np_array.png](https://numpy.org/doc/stable/_images/np_array.png)
- Or an empty array can be made, with the *empty* function (`np.empty([num_of_elements])`)
- Or an array made of a range of numbers, with *arange* (`np.arange([range])`)
- Or an area with linearly spaced values, with *linspace* (`np.linspace(0,10, num=5)`)
	- returns `array([ 0. ,  2.5,  5. ,  7.5, 10. ])`
### Specifying data type
- Default data type is floating point (*np.float64*)
- Specify which data type is desired using the *dtype* keyword
```python
>>> x = np.ones(2, dtype=np.int64)
>>> x
```
(returns `array([1, 1])`)
## Adding/Removing/Sorting Elements
- Sort with *sort* – `np.sort(arr)`
	- Find more about *sort* [[https://numpy.org/doc/stable/reference/generated/numpy.sort.html#numpy.sort "numpy.sort"]].
```python
arr = np.array([2, 1, 5, 3, 7, 4, 6, 8])
np.sort(arr)

#array([1, 2, 3, 4, 5, 6, 7, 8])
```
- Concatenate with *concatenate*
```python
a = np.array([1, 2, 3, 4])
b = np.array([5, 6, 7, 8])

#array([1, 2, 3, 4, 5, 6, 7, 8])

x = np.array([[1, 2], [3, 4]])
y = np.array([[5, 6]])

#array([[1, 2],
#       [3, 4],
#       [5, 6]])
```
## Finding the size and shape of an array
- `ndarray.ndim` will tell you the number of axes, or dimensions, of the array.
- `ndarray.size` will tell you the total number of elements of the array. This is the _product_ of the elements of the array’s shape.
- `ndarray.shape` will display a tuple of integers that indicate the number of elements stored along each dimension of the array. If, for example, you have a 2-D array with 2 rows and 3 columns, the shape of your array is `(2, 3)`.
## Reshaping an array
- Use `arr.reshape`
- Make sure the new array has the same number of elements
```python
a = np.arange(6)
# a is [0 1 2 3 4 5]
b = a.reshape(3, 2)
""" b looks like:
[[0 1]
 [2 3]
 [4 5]]
"""
```
## Adding new axes to array
- Using `np.newaxis` will increase the dimensions of your array by one dimension when used once. This means that a 1D array will become a 2D array, a 2D array will become a 3D array, and so on.
```python
a = np.array([1, 2, 3, 4, 5, 6])
a2 = a[np.newaxis, :]
a2.shape
# (1,6)

row_vector = a[np.newaxis, :]
row_vector.shape
# (1,6)

col_vector = a[:, np.newaxis]
col_vector.shape
# (6,1)
```
## Indexing and slicing
- They can be indexed and sliced in the same way as Python lists
- There are also others things you can do:
```python
data = np.array([1, 2, 3])
data[1]
# 2
print(a[a < 5])
# [1 2 3 4]

c = a[(a > 2) & (a < 11)]
print(c)
# [ 3  4  5  6  7  8  9 10]

five_up = (a > 5) | (a == 5)
print(five_up)

"""
[[False False False False]
 [ True  True  True  True]
 [ True  True  True True]]
"""
```
- keep in mind you need to use `&` and `|` not `or` and `and`
## Making arrays from existing data
- use `vstack(arr1, arr2)` and `hstack(arr1, arr2)`
- You can also use `copy` to make a copy
## Basic array operations
- You can add, subtract, multiply, and divide arrays
- Think of them like matrices
- use `ndarray.sum()` to find the sum of values
## Broadcasting
- a mechanism that allows NumPy to perform operations on arrays of different shapes
- This is what you use when you want to multiply arrays of different sizes or a vector and a scalar.
## Boolean Operators
- use `np.logical_and`, `np.logical_or`, etc.
## Looping
- Loop over a 2D numpy array using `np.nditer`
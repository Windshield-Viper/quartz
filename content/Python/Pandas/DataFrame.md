A *DataFrame* is a 2-dimensional labeled data structure with columns of potentially different types.

It can be made from:
- Dict of 1D ndarrays, lists, or dicts
- [Structured or record](https://numpy.org/doc/stable/user/basics.rec.html) [[Array Basics |NumPy Array]]
- A [[Series]]
- Another [[https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html#pandas.DataFrame "pandas.DataFrame"]]
- CSVs

- If you pass an index and / or columns, you are guaranteeing the index and / or columns of the resulting DataFrame. **Thus, a dict of Series plus a specific index will discard all data not matching up to the passed index.**

![[Other/Images, Other Attachments/Pasted image 20230524193416.png]]


- Use the *loc* attribute to return one or more rows (more info on *loc*: [[Indexing, Selecting, Assigning]]) 
```python
import pandas as pd  
  
data = {  
  "calories": [420, 380, 390],  
  "duration": [50, 40, 45]  
}  
  
#load data into a DataFrame object:  
df = pd.DataFrame(data)  
  
print(df.loc[0])
```
In the above case, the original DF is:  

|     | Calories | Duration |
| --- | -------- | -------- |
| 0   | 420      | 50       |
| 1   | 380      | 40       |
| 2   | 390      | 45       |

The *loc* command will return:  

| Calories | 420 |
| -------- | --- |
| Duration | 50  |         |     |

Note that this is a Series.

You can also run:
```python
print(df.loc[[0, 1]])
```
This returns:  

|     | calories | duration |
| -- | ------- | ------- |
| 0   | 420      | 50       |
| 1   | 380      | 40         |

(Note that this is a DataFrame).

The *index* command lets you make your own indexes.
```python
df = pd.DataFrame(data, index = ["day1", "day2", "day3"])
#this just replaces the 0, 1, and 2 with "day1," "day2", and "day3"
```
Named indices can be indexed like unnamed ones with *loc*.

CSV files can be turned into Pandas DataFrames like so:
```python
import pandas as pd  
  
df = pd.read_csv('data.csv')  
  
print(df)
```

## How would an actual DataFrame look?
Creating a [[https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html#pandas.DataFrame "pandas.DataFrame"]] by passing a NumPy array, with a datetime index using [[https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.date_range.html#pandas.date_range "pandas.date_range"]] and labeled columns:  
![[Other/Images, Other Attachments/Pasted image 20230524194059.png]]
## More simple DataFrame practice
- a dataframe that looks like this:  
![[Other/Images, Other Attachments/Pasted image 20230610210850.png]]
```python
fruits = pd.DataFrame({"Apples": [30], "Bananas": [21]}, index=[0])
```
- looks like this:  
![[Other/Images, Other Attachments/Pasted image 20230610211013.png]]
```python
fruit_sales = pd.DataFrame({"Apples": [35, 41], "Bananas": [21, 34]}, index=["2017 Sales", "2018 Sales"])
```
- looks like this:  
![[Other/Images, Other Attachments/Pasted image 20230610211117.png]]
```python
ingredients = pd.Series(["4 cups", "1 cup", "2 large", "1 can"], index=["Flour", "Milk", "Eggs", "Spam"], name="Dinner")
```

## CSVs
- read a CSV into a Dataframe w/ index as the first column:
```python
reviews = pd.read_csv("../input/wine-reviews/winemag-data_first150k.csv", index_col=0)
```
- save a dataframe called *animals* into a csv:
```python
animals.to_csv("cows_and_goats.csv")
```

## Looping over a DataFrame
- Iterating over a Pandas DataFrame is typically done with the `iterrows()` method. Used in a for loop, every observation is iterated over and on every iteration the row label and actual row contents are available:
```python
for lab, row in brics.iterrows() :
    ...
```
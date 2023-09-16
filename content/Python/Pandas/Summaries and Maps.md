# Summary Functions
## Describe
- `df.column.describe()`
- Returns a high-level summary of the attributes of the given column
## Mean
- `df.column.mean()`
- Returns mean of all vals in column
## Unique
- `df.column.unique()`
- Lists all unique vals in a column
## Value_Counts
- `df.column.value_counts()`
- Count how many of each value in a column
# Maps
## Map()
- Creating a new thing from existing data
- Applying a function to a column of values
- Example:
```python
review_points_mean = reviews.points.mean()
reviews.points.map(lambda p: p - review_points_mean)
```
## Apply()
- The same thing as `map`, but on an entire DataFrame.
- Calls a custom method on each row.
- Example:
```python
def remean_points(row):
    row.points = row.points - review_points_mean
    return row

reviews.apply(remean_points, axis='columns')
```
## Quick Maps
- These are just there to make remapping more convenient.
- Example of quick remeaning:
```python
review_points_mean = reviews.points.mean()
reviews.points - review_points_mean
```
- Example of quick joining of two Series of equal length:
```python
reviews.country + " - " + reviews.region_1
```
(here, the output looks like:)
![[Other/Images, Other Attachments/Pasted image 20230702153957.png| 400]]


TBD: review `idmax`
- Use `rename` to rename a column or index, as in `reviews.rename(columns={'points': 'score'})`
- Rename axes using `rename_axis`, as in `reviews.rename_axis("wines", axis='rows').rename_axis("fields", axis='columns')`
- Use `concat` to concatenate two DataFrames, like `pd.concat([canadian_youtube, british_youtube])`
- Use `join` for more control, like if you want to only join things that have an index in common. Example:
```python
left = canadian_youtube.set_index(['title', 'trending_date'])
right = british_youtube.set_index(['title', 'trending_date'])

left.join(right, lsuffix='_CAN', rsuffix='_UK')
```

# Basic overview pictures
## Loc
![[Other/Images, Other Attachments/Pasted image 20230802132233.png| 500]]

- You can access things in DataFrames in a variety of ways.
# Native Accessors
- These are things that are native to Python and so they are not additions to Python from the Pandas library
- Find a column in these ways:
	- `name.column`
	- `name['column']`
- Find a specific value:
	- `name['column'][num_in_column]`
# Index Based Selection
- Selects data based on its numerical position in the dataset. `iloc` follows this paradigm.
- Example: `name.iloc[0]` returns the first row of the dataset
- Same with columns, but slightly different: `name.iloc[:, 0]` returns the first columns
- Use the colon to select certain values. Negative numbers select from the back.
# Label Based Selection
- This is often simpler and uses `loc`.
- `name.loc[x, y]` returns the thing at position x, y
- Example:
![[Other/Images, Other Attachments/Pasted image 20230701203257.png|300]]
# Indexing Differences
- `loc` uses standard indexing while `iloc` does not. Keep this in mind.
![[Other/Images, Other Attachments/Pasted image 20230701203625.png| 400]]
# Using logic
- With loc, you can use logic to select only certain values in the dataset. 
- E1: `name.loc[name.color == 'Blue']`
- E2: `name.loc[(name.color == 'Blue']) &  (name.loc[name.food == 'pasta'])
- E3: `reviews.loc[reviews.country.isin(['Italy', 'France'])]`
- E4: `reviews.loc[reviews.price.notnull()]`
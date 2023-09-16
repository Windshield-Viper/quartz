# Groupwise Analysis
- here is an alternative to the `value_counts()` function using groupwise analysis: `reviews.groupby('points').points.count()`
- `groupby` makes a group from the original DF.
- These groups can be used in a variety of ways.
- example: `reviews.groupby('points').price.min()` gives you
![[Other/Images, Other Attachments/Pasted image 20230706141358.png| 400]]
This puts everything into groups of `points` and then does something to them.
- Use `apply()` to access the new DataFrame created. Example, to find the first value from a certain column value (as in, the first wine from a certain winery) – `reviews.groupby('winery').apply(lambda df: df.title.iloc[0])`
- You can group by more than one category. For example, you could group by both `country` and `province`, leaving you with something like 
![[Other/Images, Other Attachments/Pasted image 20230706141918.png| 350]]
- use `agg` to run multiple functions on the DataFrame at the same time. Example – `reviews.groupby(['country']).price.agg([len, min, max])`
- The previously mentioned case where you group by multiple countries created something called a *multi-index*. To fix this issue, you can run `reset_index()` on the DF in question.
# Sort_Values
- You can use `sort_values` to sort things by one of the columns. Example: `countries_reviewed.sort_values(by='len')`.
- It is ascending by default but that can be changed.
- You can sort by more than one thing at a time. For each one, you can choose whether to sort ascending or descending.
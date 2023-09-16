# Overview
Time complexity is calculated using Big O notation, expressing the worst-case TC as n gets larger.

- In Big O notation, complexity is denoted as $O(f(n))$.
- Any constant factors/lower order terms are omitted, so anything that runs in constant time is called $O(1)$.
```python
a = 5
b = 7
c = 4
d = a + b + c + 153
```
- The time complexity of loops is the number of iterations that the loop runs.
```python
i = 0

while i < n:
	# constant time code here
	i += 1
```
- Lower order terms are ommitted so this is also $O(n)$:
```python
for i in range(5 * n + 17):
	pass  # constant time code here
```
- Time complexity of multiple loops is found by multiplying the number of iterations of inner and outer loops.
- If an algorithm contains multiple blocks, then its time complexity is the worst time complexity out of any block.
- If an algorithm has multiple blocks of the same order, just add the time complexities.
# Common Complexities
![[Other/Images, Other Attachments/Pasted image 20230803221356.png]]
# Upper Bounds on Value of N for Each Time Complexity
![[Other/Images, Other Attachments/Pasted image 20230803221445.png]]
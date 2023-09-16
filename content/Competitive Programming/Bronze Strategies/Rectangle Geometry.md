- Keep in mind that for simple cases of problems like this, it always helps to draw out a solution on paper.

> [!NOTE] Representing rectangles  
> A rectangle can be represented with $2$ points: its top right corner and bottom left corner.  
These points are labeled $tr$ (top right) and $bl$ (bottom left).

## Common Formulas
### Finding area
$\texttt{length}$ is the length of the vertical sides, and $\texttt{width}$ is the length of the horizontal sides.

$\texttt{width} = \texttt{tr}_x - \texttt{bl}_x$  
$\texttt{length} = \texttt{tr}_y - \texttt{bl}_y$  
$\texttt{area} = \texttt{width} \cdot \texttt{length}$

```python
def area(bl_x: int, bl_y: int, tr_x: int, tr_y: int) -> int:
	length = tr_y - bl_y
	width = tr_x - bl_x
	return length * width
```

### Checking for intersection
- Given two rectangles $a$ and $b$, there are only two cases where they do not intersect:
	- $\texttt{tr}_{a_y}$ $\leq$ $\texttt{bl}_{b_y}$ or $\texttt{bl}_{a_y}$ $\geq$ $\texttt{tr}_{b_y}$.
	- $\texttt{bl}_{a_x}$ $\geq$ $\texttt{tr}_{b_x}$ or $\texttt{tr}_{a_x}$ $\leq$ $\texttt{bl}_{b_x}$.  
In other words, they don’t intersect if the top right of one rectangle is below the bottom left of the other or if the top right of one is to the left of the bottom left of the other.  

In all other cases, the rectangles intersect.

```python
def intersect(s1, s2) -> bool:
	bl_a_x, bl_a_y, tr_a_x, tr_a_y = s1[0], s1[1], s1[2], s1[3]
	bl_b_x, bl_b_y, tr_b_x, tr_b_y = s2[0], s2[1], s2[2], s2[3]
	
	# no overlap
	if bl_a_x >= tr_b_x or tr_a_x <= bl_b_x or bl_a_y >= tr_b_y or tr_a_y <= bl_b_y:
		return False
	else:
		return True
```

### Finding area of intersection
Assuming that such an intersection is itself a rectangle:
- First, find this rectangle's length and width. 
	- $\texttt{width} = \min(\texttt{tr}_{a_x}, \texttt{tr}_{b_x}) - \max(\texttt{bl}_{a_x}, \texttt{bl}_{b_x})$. $\texttt{length} = \min(\texttt{tr}_{a_y}, \texttt{tr}_{b_y}) - \max(\texttt{bl}_{a_y}, \texttt{bl}_{b_y})$.
- If either of these values are negative, the rectangles do not intersect. If they are zero, the rectangles intersect at a single point. 
- Multiply the length and width to find the overlapping area.
```python
def inter_area(s1, s2) -> int:
	bl_a_x, bl_a_y, tr_a_x, tr_a_y = s1[0], s1[1], s1[2], s1[3]
	bl_b_x, bl_b_y, tr_b_x, tr_b_y = s2[0], s2[1], s2[2], s2[3]
	
    return (min(tr_a_x, tr_b_x) - max(bl_a_x, bl_b_x)) * (min(tr_a_y, tr_b_y) - max(bl_a_y, bl_b_y))
```

---
dg-publish: true
introduced-in: section 2
---
#calc/concept 
## Definition of a derivative
The derivative of the function $f$ with respect to the variable $x$ is the function $f'$ whose value at $x$ is $\displaystyle f'(x)= \lim_{ h \to 0 } \frac{f(x+h)-f(x)}{h}$ 
## Slope of a curve at a point
- The slope of the curve $y=f(x)$ at the point $(a, f(a))$ is $\displaystyle m= \lim_{ h \to 0 } \frac{f(a+h)-f(a)}{h}$  
	- (This is also the equation for the slope of the tangent to $y=f(x)$ at that point)
- The **normal line** to a curve at a point is the line perpendicular to a tangent at that point.
## Shortcut for polynomial derivatives
If you have a polynomial of the form $y=x^n$, its derivative is $y'=nx^{n-1}$ for each term of the polynomial. This is good for verification but limit notation should still be used in work.
### Example
For $x^3-2x^2+3x-4$, the derivative comes out to be (term-by-term) $y'=3x^2-4x^1+3x^0-0$, simplifying to $y'=3x^2+4x+3$.

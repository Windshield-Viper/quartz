A set of results that relate the coefficients of a [polynomial](https://artofproblemsolving.com/wiki/index.php/Polynomial "Polynomial") to its roots. In particular, they state that the [elementary symmetric polynomials](https://artofproblemsolving.com/wiki/index.php/Elementary_symmetric_polynomial "Elementary symmetric polynomial") (the sum, pairwise sum, triple-wise sum, etc) of 
its roots can be easily expressed as a ratio between two of the polynomial's coefficients.
## Statement
Let $P(x) = a_n x^n + a_{n-1}x^{n-1} + \cdots + a_1 x + a_0$ be any polynomial with complex coefficients with roots $r_1, r_2, \ldots , r_n$, and let $s_j$ be the $j^{\text{th}}$ elementary symmetric polynomial of the roots.

Vieta’s formulas then state that $$s_1 = r_1 + r_2 + \cdots + r_n = - \frac{a_{n-1}}{a_n}$$$$s_2 = r_1r_2 + r_1r_3 + \cdots + r_{n-1}r_n = \frac{a_{n-2}}{a_n}$$ and so on until:
$$s_n = r_1r_2r_3 \cdots r_n = (-1)^n \frac{a_0}{a_n}$$

This can be compactly summarized as $s_j = (-1)^j \frac{a_{n-j}}{a_n}$ for some $j$ such that $1 \leq j \leq n$.
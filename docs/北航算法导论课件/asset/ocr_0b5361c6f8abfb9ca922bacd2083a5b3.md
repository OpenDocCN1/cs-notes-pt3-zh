# 30.1.1 Coefficient representation

+   - **A *coefficient representation* of a polynomial** $A(x) = \sum_{j=0}^{n-1} a_j x^j$
+     $a = (a_0, a_1, ..., a_{n-1})^T$, column vectors
+   - **Convenient for certain operations. For example,**
+     - *evaluating $A(x)$ at a given point $x_0$, takes time $\Theta(n)$* using *Horner's rule*:
+       $A(x_0) = a_0 + x_0(a_1 + x_0(a_2 + \cdots + x_0(a_{n-2} + x_0(a_{n-1}))))$
+     - *adding two polynomials represented $a = (a_0, a_1, ..., a_{n-1})^T$ and $b = (b_0, b_1, ..., b_{n-1})^T$, takes $\Theta(n)$ time*: we just produce the coefficient vector $c = (c_0, c_1, ..., c_{n-1})$, where $c_j = a_j + b_j$ for $j = 0, 1, ..., n - 1$.
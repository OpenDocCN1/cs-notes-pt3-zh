# Matrix Boolean product

+   - A *Boolean product* of two matrices is similar to matrix multiplication

$c_{1,1}=a_{1,1}*b_{1,1}+a_{1,2}*b_{2,1}+a_{1,3}*b_{3,1}+a_{1,4}*b_{4,1}$

+   - Instead of the sum of the products, it’s the conjunction (and) of the disjunctions (ors)

$c_{1,1}=a_{1,1}\land b_{1,1}\lor a_{1,2}\land b_{2,1}\lor a_{1,3}\land b_{3,1}\lor a_{1,4}\land b_{4,1}$

+   - Denoted by the or symbol: $\odot$

$\begin{bmatrix}1&0&0&0\\0&1&0&0\\1&0&1&0\\1&0&1&0\end{bmatrix}\odot\begin{bmatrix}0&1&1&0\\0&1&1&0\\0&0&1&1\\1&1&0&0\end{bmatrix}=\begin{bmatrix}0&1&1&0\\0&1&1&0\\0&1&1&1\\0&1&1&1\end{bmatrix}$
# Polynomials multiplication〔多项式相乘〕

+   - **A(x), B(x), degree-bound n**    $A(x)=\sum_{j=0}^{n-1} a_j x^j$ and $B(x)=\sum_{j=0}^{n-1} b_j x^j$
+   - **C(x) = A(x)B(x), degree-bound 2n-1**

Another way to express the product C(x) is

$C(x)=\sum_{j=0}^{2n-2} c_j x^j$    (30.1)

where $c_j = \sum_{k=0}^{j} a_k b_{j-k}$    (30.2)

Note that degree(C) = degree(A) + degree(B), implying degree-bound(C) = degree-bound(A) + degree-bound(B) -1 ≤ degree-bound(A) + degree-bound(B). We also say: degree-bound(C)=degree-bound(A)+degree-bound(B)
# 30.1.1 Coefficient representation

+   - **multiplication of $A(x)$ and $B(x)$**
+   
+     $A(x)=\sum_{j=0}^{n-1}a_jx^j,\quad a=(a_1,a_2,\cdots,a_{n-1})^T;\quad B(x)=\sum_{j=0}^{n-1}b_jx^j,\quad b=(b_1,b_2,\cdots,b_{n-1})^T$
+   
+     $C(x)=\sum_{j=0}^{2n-2}c_jx^j$ \hfill (30.1)
+   
+     where $c_j=\sum_{k=0}^{j}a_kb_{j-k}$ \hfill (30.2)

+   - takes time $\Theta(n^2)$, why?

+   - more difficult than adding two polynomials.

+   - coefficient vector $c$, given by equation (30.2), is also called the *convolution* [卷积] of $a$ and $b$, denoted $c=a\odot b$.

+   - Multiplying polynomials and computing convolutions are fundamental computational problems, and important.
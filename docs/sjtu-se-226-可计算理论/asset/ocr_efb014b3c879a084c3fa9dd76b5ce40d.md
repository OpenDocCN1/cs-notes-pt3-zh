# Effective Denumerable Set

4. If $x > 0$ then it has a unique expression as

$$x = 2^{u_1} + 2^{u_1+u_2+1} + \ldots + 2^{u_1+u_2+\ldots+u_k+k-1}.$$

The function $a(i,x) = a_i$ is primitive recursive:

$$a(i,x)=b(i,x),\quad \text{if } i=0 \text{ or } i=1,$$

$$a(i+1,x)=\bigl(b(i+1,x)-b(i,x)\bigr)-1,\quad \text{if } i\geq 1.$$

We conclude that $a_1,a_2,a_3,\ldots,a_k$ can be calculated by primitive recursive functions.
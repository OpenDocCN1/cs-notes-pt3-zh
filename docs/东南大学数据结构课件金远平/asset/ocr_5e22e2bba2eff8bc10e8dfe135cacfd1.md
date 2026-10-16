# Lemma 5.6 [Tarjan and Van Leeuwen]: Assume we start with a forest of trees, each having one node. Let T(f, u) be the maximum time required to process any intermixed sequence of f finds and u unions. Assume u ≥ n/2, then

$$k_1(n+f\,\alpha(f+n,n)) \le T(f,u) \le k_2(n+f\,\alpha(f+n,n))$$

For some positive constants $k_1$ and $k_2$.

Note T(f, u) is not linear even though $\alpha(f+n,n)$ grows very slow.

The space requirements are one node for each element.
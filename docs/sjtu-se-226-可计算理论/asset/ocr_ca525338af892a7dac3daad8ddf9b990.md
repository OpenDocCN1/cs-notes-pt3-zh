# Effective Denumerable Set

A number $x \in \mathbb{N}$ has a unique expression as

$$x = \sum_{i=0}^{\infty} \alpha_i 2^i.$$

where $\alpha_i$ is either $0$ or $1$ for all $i \ge 0$.

+   1. The function $\alpha(i,x) = \alpha_i$ is primitive recursive:
+   
+   $$\alpha(i,x) = \text{rm}(2, \text{qt}(2^i, x)).$$

+   2. The function $\ell(x) = \text{if } x > 0 \text{ then } k \text{ else } 0$ is primitive recursive:
+   
+   $$\ell(x) = \sum_{i < x} \alpha(i,x).$$
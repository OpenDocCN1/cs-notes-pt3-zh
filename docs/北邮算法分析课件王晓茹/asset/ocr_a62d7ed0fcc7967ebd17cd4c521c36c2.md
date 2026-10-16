【Definition】 $T(N) = O(f(N))$ if there are positive constants $c$ and $n_0$ such that $T(N) \leq c f(N)$ for all $N \geq n_0$.

【Definition】 $T(N) = \Omega(g(N))$ if there are positive constants $c$ and $n_0$ such that $T(N) \geq c g(N)$ for all $N \geq n_0$.

【Definition】 $T(N) = \Theta(h(N))$ if and only if $T(N) = O(h(N))$ and $T(N) = \Omega(h(N))$.

【Definition】 $T(N) = o(p(N))$ if $T(N) = O(p(N))$ and $T(N) \neq \Theta(p(N))$.

# Note:

+   > $2N + 3 = O(N) = O(N^{k \geq 1}) = O(2^N) = \dots$ We shall always take the smallest $f(N)$.

+   > $2^N + N^2 = \Omega(2^N) = \Omega(N^2) = \Omega(N) = \Omega(1) = \dots$ We shall always take the largest $g(N)$.
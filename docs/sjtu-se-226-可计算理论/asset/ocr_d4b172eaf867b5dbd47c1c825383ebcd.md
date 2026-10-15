# Definability of Composition

Let $F, G_1, \ldots, G_k$ be programs that compute $f, g_1, \ldots, g_k$.

Let $m = \max\{n, k, \rho(F), \rho(G_1), \ldots, \rho(G_k)\}$.

Registers:

$[\ldots]_1^{[m]}[\bar{x}]_{m+n}[g_1(\bar{x})]_{m+n+1}\ldots[g_k(\bar{x})]_{m+n+k}$
# OPT BST

Optimal substructure & overlapping subproblems

e[i,j]: The cost of optimal binary search tree for $k_i, k_{i+1}, ..., k_j$

| d0 | k1 | d1 | k2 | d2 | k3 | d3 | k4 | d4 | k5 | d5 |
|---|---|---|---|---|---|---|---|---|---|---|
| 0.05 | 0.15 | 0.10 | 0.10 | 0.05 | 0.05 | 0.05 | 0.10 | 0.05 | 0.20 | 0.10 |

e[i,j] = q_j if j = i-1

e[i,j] = min_{i<=r<=j}{e[i,r-1] + e[r+1,j] + w[i,j]} if j >= i

where

w[i,j] = q_i if j = i-1

w[i,j] = w[i,r-1] + w[r+1,j] + p_r if j >= i
# # Recursive formulation

# ## Theorem.

\(c[i, j] = \begin{cases} c[i-1, j-1] + 1 & \text{if } x[i] = y[j], \\ \max \{ c[i-1, j], c[i, j-1] \} & \text{otherwise.} \end{cases}\)

# ### Proof. Case \(x[i] = y[j]\):

![](bbox=[0.121, 0.491, 0.846, 0.729])

Let \(z[1 \dots k] = \text{LCS}(x[1 \dots i], y[1 \dots j])\), where \(c[i, j] = k\). Then, \(z[k] = x[i]\), or else \(z\) could be extended. Thus, \(z[1 \dots k-1]\) is CS of \(x[1 \dots i-1]\) and \(y[1 \dots j-1]\).
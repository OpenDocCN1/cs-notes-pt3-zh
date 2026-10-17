# # Identifying subproblems

+   - The number of orders of multiplications equal to the number of parenthesization

P(q) = \begin{cases} 1 & \text{if } q = 2 \\ \sum_{k=1}^{q-1} p(k)p(q-k) & \text{if } q \ge 2 \end{cases} \quad T(q) \approx O(4^q q^{3/2}) \quad \approx O(2^q)

+   - In fact, a particular parenthesization can be represented by a binary tree

+   - The leaves corresponds to matrices
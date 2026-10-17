# # Tighter analysis (continued)

Cost of \(n\) insertions \( = \sum_{i=1}^{n} c_i \)
\(\leq n + \sum_{j=0}^{\lfloor \lg(n-1) \rfloor} 2^j \)
\(\leq 3n \)
\( = \Theta(n) \).

Thus, the average cost of each dynamic-table operation is \(\Theta(n)/n = \Theta(1)\).
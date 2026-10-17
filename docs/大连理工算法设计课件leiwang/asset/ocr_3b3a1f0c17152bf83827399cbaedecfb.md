# # The amortized costs bound the true costs

The total amortized cost of \( n \) operations is

\(\sum_{i=1}^n \hat{c}_i = \sum_{i=1}^n \left(c_i + \Phi(D_i) - \Phi(D_{i-1})\right)\)

\(= \sum_{i=1}^n c_i + \Phi(D_n) - \Phi(D_0)\)

\(\ge \sum_{i=1}^n c_i \quad \text{since } \Phi(D_n) \ge 0 \text{ and } \Phi(D_0) = 0.\)
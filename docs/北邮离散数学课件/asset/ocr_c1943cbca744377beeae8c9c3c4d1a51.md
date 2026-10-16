# Greedy Change-Making Algorithm

+   - Optimality depends on the denominations available.
+   - For U.S. coins, optimality still holds if we add half dollar coins (50 cents) and dollar coins (100 cents).
+   - But if we allow only quarters (25 cents), dimes (10 cents), and pennies (1 cent), the algorithm no longer produces the minimum number of coins.
+   - Consider the example of 31 cents. The optimal number of coins is 4, i.e., 3 dimes and 1 penny. What does the algorithm output?
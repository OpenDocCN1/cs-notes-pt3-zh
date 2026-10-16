# 17.2 The accounting method

+   - **Amortized cost** : the amount we charge an operation.
+     - **credit** : when an operation’s amortized cost exceeds its actual cost, we assign the difference to specific objects in the data structure as credit.
+     - Credit can help pay for later operations whose amortized cost is less than their actual cost

+   - We denote the actual cost of the *i*th operation by $c_i$ and the amortized cost of the *i*th operation by $\widehat{c_i}$, we require
+   
+     $$\sum_{i=1}^{n} \widehat{c_i} \ge \sum_{i=1}^{n} c_i$$
+   
+     for all sequences of $n$ operations.

+   - The total credit $\sum_{i=1}^{n} \widehat{c_i} - \sum_{i=1}^{n} c_i$
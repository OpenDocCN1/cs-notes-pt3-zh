# Introduction (Cont.)

+   - Cost difference between evaluation plans for a query can be enormous
+     - E.g. seconds vs. days in some cases

+   - Steps in **cost-based query optimization**
+     1. Generate logically equivalent expressions using **equivalence rules**
+     2. Annotate resultant expressions to get alternative query plans
+     3. Choose the cheapest plan based on **estimated cost**

+   - Estimation of plan cost based on:
+     - Statistical information about relations. Examples:
+       - number of tuples, number of distinct values for an attribute
+     - Statistics estimation for intermediate results
+       - to compute cost of complex expressions
+     - Cost formulae for algorithms, computed using statistics
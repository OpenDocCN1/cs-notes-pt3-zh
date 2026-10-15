# Converting Non-Binary Relationships to Binary Form

In general, any non-binary relationship can be represented using binary relationships by creating an artificial entity set.

+   - Replace R between entity sets A, B and C by an entity set E, and three relationship sets:
+     1. R_A relating E and A
+     2. R_B relating E and B
+     3. R_C relating E and C

+   - Create a special identifying attribute for E

+   - Add any attributes of R to E

+   - For each relationship (a_i, b_i, c_i) in R, create
+     1. a new entity e_i in the entity set E
+     2. add (e_i, a_i) to R_A
+     3. add (e_i, b_i) to R_B
+     4. add (e_i, c_i) to R_C

![](bbox=[0.18, 0.73, 0.38, 0.92])

![](bbox=[0.48, 0.62, 0.92, 0.88])
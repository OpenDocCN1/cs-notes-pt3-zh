# Transformation of Relational Expressions

+   - Two relational algebra expressions are said to be **equivalent** if the two expressions generate the same set of tuples on every *legal* database instance
+     - Note: order of tuples is irrelevant
+     - we don’t care if they generate different results on databases that violate integrity constraints
+   - In SQL, inputs and outputs are multisets of tuples
+     - Two expressions in the multiset version of the relational algebra are said to be equivalent if the two expressions generate the same multiset of tuples on every legal database instance.
+   - An **equivalence rule** says that expressions of two forms are equivalent
+     - Can replace expression of first form by second, or vice versa
# Use of Multivalued Dependencies

+   - We use multivalued dependencies in two ways:
+     1. To test relations to **determine** whether they are legal under a given set of functional and multivalued dependencies
+     2. To specify **constraints** on the set of legal relations. We shall thus concern ourselves *only* with relations that satisfy a given set of functional and multivalued dependencies.

If a relation r fails to satisfy a given multivalued dependency, we can construct a relations r′ that does satisfy the multivalued dependency by adding tuples to r.

![](bbox=[0.0, 0.04, 0.07, 0.14])
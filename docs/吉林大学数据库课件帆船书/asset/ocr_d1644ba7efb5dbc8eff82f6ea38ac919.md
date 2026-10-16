# Multiquery Optimization

+   Example
+   Q1: **select * from** (r **natural join** t) **natural join** s
+   Q2: **select * from** (r **natural join** u) **natural join** s

+   Both queries share common subexpression (r natural join s)

+   May be useful to compute (r natural join s) once and use it in both queries

+   But this may be more expensive in some situations

+   e.g. (r natural join s) may be expensive, plans as shown in queries may be cheaper

+   **Multiquery optimization**: find best overall plan for a set of queries, expoiting sharing of common subexpressions between queries where it is useful
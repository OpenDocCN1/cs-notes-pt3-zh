# Safety of Expressions

+   - It is possible to write tuple calculus expressions that generate infinite relations.
+   - For example, { t | ¬ t ∈ r } results in an infinite relation if the domain of any attribute of relation r is infinite
+   - To guard against the problem, we restrict the set of allowable expressions to safe expressions.
+   - An expression { t | P ( t ) } in the tuple relational calculus is safe if every component of t appears in one of the relations, tuples, or constants that appear in P
+     - NOTE: this is more than just a syntax condition.
+       - E.g. { t | t[A] = 5 ∨ true } is not safe --- it defines an infinite set with attribute values that do not appear in any relation or tuples or constants in P.

![](bbox=[0.0, 0.03, 0.08, 0.15])
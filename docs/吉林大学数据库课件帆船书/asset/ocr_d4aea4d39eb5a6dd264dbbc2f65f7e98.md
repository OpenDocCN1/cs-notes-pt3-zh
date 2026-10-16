# The Power of Recursion

+   - Recursive views make it possible to write queries, such as transitive closure queries, that cannot be written without recursion or iteration.
+     - Intuition: Without recursion, a non-recursive non-iterative program can perform only a fixed number of joins of *prereq* with itself
+       - This can give only a fixed number of levels of managers
+       - Given a fixed non-recursive query, we can construct a database with a greater number of levels of prerequisites on which the query will not work
+       - Alternative: write a procedure to iterate as many times as required
+         - See procedure *findAllPrereqs* in book
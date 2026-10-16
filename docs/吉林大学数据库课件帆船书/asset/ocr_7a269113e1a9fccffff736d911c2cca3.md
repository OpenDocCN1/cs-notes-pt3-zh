# Structure of Query Optimizers

+   - Many optimizers considers only left-deep join orders.
+     - Plus heuristics to push selections and projections down the query tree
+     - Reduces optimization complexity and generates plans amenable to pipelined evaluation.
+   - Heuristic optimization used in some versions of Oracle:
+     - Repeatedly pick “best” relation to join next
+       - Starting from each of n starting points. Pick best among these
+   - Intricacies of SQL complicate query optimization
+     - E.g. nested subqueries
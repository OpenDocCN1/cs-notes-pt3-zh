# Parametric Query Optimization

+   Example
+   select *
+   from r natural join s
+   where r.a < $1

+   value of parameter $1 not known at compile time
+   known only at run time

+   different plans may be optimal for different values of $1

+   Solution 1: optimize at run time, each time query is submitted
+   can be expensive

+   Solution 2: Parametric Query Optimization:
+   optimizer generates a set of plans, optimal for different values of $1
+   Set of optimal plans usually small for 1 to 3 parameters
+   Key issue: how to do find set of optimal plans efficiently
+   best one from this set is chosen at run time when $1 is known

+   Solution 3: Query Plan Caching
+   If optimizer decides that same plan is likely to be optimal for all parameter values, it caches plan and reuses it, else reoptimize each time
+   Implemented in many database systems
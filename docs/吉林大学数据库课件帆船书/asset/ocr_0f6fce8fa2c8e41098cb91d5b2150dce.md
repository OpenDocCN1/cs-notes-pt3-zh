# Ranking (Cont.)

+   - For a given constant *n*, the ranking the function *ntile(n)* takes the tuples in each partition in the specified order, and divides them into *n* buckets with equal numbers of tuples.
+   - E.g.,
+     ```sql
+     select ID, ntile(4) over (order by GPA desc) as quartile
+     from student_grades;
+     ```
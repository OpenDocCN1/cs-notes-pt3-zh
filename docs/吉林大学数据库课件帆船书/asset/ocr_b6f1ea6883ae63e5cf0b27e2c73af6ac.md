# Multiple-Key Access

+   - Use multiple indices for certain types of queries.
+   - Example:
+     **select** *ID*
+     **from** *instructor*
+     **where** *dept_name* = “Finance” **and** *salary* = 80000
+   - Possible strategies for processing query using indices on single attributes:
+     1. Use index on *dept_name* to find instructors with department name Finance; test *salary* = 80000
+     2. Use index on *salary* to find instructors with a salary of $80000; test *dept_name* = “Finance”.
+     3. Use *dept_name* index to find pointers to all records pertaining to the “Finance” department. Similarly use index on *salary*. Take intersection of both sets of pointers obtained.

![](bbox=[0.0, 0.04, 0.09, 0.15])
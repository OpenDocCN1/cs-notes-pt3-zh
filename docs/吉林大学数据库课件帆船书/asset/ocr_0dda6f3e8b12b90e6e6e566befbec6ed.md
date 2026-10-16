# Ordering the Display of Tuples

+   List in alphabetic order the names of all instructors
+   
+   select distinct name
+   from instructor
+   order by name

+   We may specify desc for descending order or asc for ascending order, for each attribute; ascending order is the default.
+   
+   Example: order by name desc

+   Can sort on multiple attributes
+   
+   Example: order by dept_name, name
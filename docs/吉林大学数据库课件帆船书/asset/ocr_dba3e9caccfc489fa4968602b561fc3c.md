# Where Clause Predicates

+   - SQL includes a **between** comparison operator
+   - Example: Find the names of all instructors with salary between $90,000 and $100,000 (that is, ≥ $90,000 and ≤ $100,000)
+     - **select** name
+       **from** instructor
+       **where** salary **between** 90000 **and** 100000
+   - Tuple comparison
+     - **select** name, course_id
+       **from** instructor, teaches
+       **where** (instructor.ID, dept_name) = (teaches.ID, 'Biology');
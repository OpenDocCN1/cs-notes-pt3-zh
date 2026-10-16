# Examples

+   Find the names of all instructors who have taught some course and the course_id
+   
+   - select name, course_id
+     from instructor , teaches
+     where instructor.ID = teaches.ID

+   Find the names of all instructors in the Art department who have taught some course and the course_id
+   
+   - select name, course_id
+     from instructor , teaches
+     where instructor.ID = teaches.ID and instructor. dept_name = ‘Art’
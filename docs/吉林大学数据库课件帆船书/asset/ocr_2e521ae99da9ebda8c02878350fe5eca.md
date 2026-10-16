# Updates with Scalar Subqueries

+   - Recompute and update tot_creds value for all students
+     ```sql
+     update student S
+     set tot_cred = (select sum(credits)
+     from takes, course
+     where takes.course_id = course.course_id and
+     S.ID= takes.ID and
+     takes.grade <> 'F' and
+     takes.grade is not null);
+     ```
+   - Sets tot_creds to null for students who have not taken any course
+   - Instead of sum(credits), use:
+     ```sql
+     case
+     when sum(credits) is not null then sum(credits)
+     else 0
+     end
+     ```
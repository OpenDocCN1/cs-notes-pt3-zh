# Use of “exists” Clause

+   Yet another way of specifying the query “Find all courses taught in both the Fall 2009 semester and in the Spring 2010 semester”
+   
+   select course_id
+   from section as S
+   where semester = 'Fall' and year = 2009 and
+       exists (select *
+               from section as T
+               where semester = 'Spring' and year= 2010
+                   and S.course_id = T.course_id);

+   Correlation name – variable S in the outer query

+   Correlated subquery – the inner query
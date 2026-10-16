# # Use of “not exists” Clause

Find all students who have taken all courses offered in the Biology department.

```
```sql
select distinct S.ID, S.name
from student as S
where not exists (
(select course_id
from course
where dept_name = 'Biology')
except
(select T.course_id
from takes as T
where S.ID = T.ID));
```
```

+   - First nested query lists all courses offered in Biology
+   - Second nested query lists all courses a particular student took

Note that X – Y = ∅ ⇔ X ⊆ Y

Note: Cannot write this query using = all and its variants
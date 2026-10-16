# Recursion in SQL

+   - SQL:1999 permits recursive view definition
+   - Example: find which courses are a prerequisite, whether directly or indirectly, for a specific course

```
with recursive rec_prereq(course_id, prereq_id) as (
    select course_id, prereq_id
    from prereq
    union
    select rec_prereq.course_id, prereq.prereq_id,
    from rec_rereq, prereq
    where rec_prereq.prereq_id = prereq.course_id
)
select *
from rec_prereq;
```

This example view, rec_prereq, is called the transitive closure of the prereq relation

Note: 1st printing of 6th ed erroneously used c_prereq in place of rec_prereq in some places
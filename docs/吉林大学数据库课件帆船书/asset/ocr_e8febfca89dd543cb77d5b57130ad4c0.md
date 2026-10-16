# Set Membership (Cont.)

Find the total number of (distinct) students who have taken course sections taught by the instructor with ID 10101

```
select count (distinct ID)
from takes
where (course_id, sec_id, semester, year) in
    (select course_id, sec_id, semester, year
    from teaches
    where teaches.ID= 10101);
```

Note: Above query can be written in a much simpler manner. The formulation above is simply to illustrate SQL features.
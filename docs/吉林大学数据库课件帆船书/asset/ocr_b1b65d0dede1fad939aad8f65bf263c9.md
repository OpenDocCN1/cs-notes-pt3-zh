# Embedded SQL (Cont.)

+   - Example:
+     - From within a host language, find the ID and name of students who have completed more than the number of credits stored in variable credit_amount in the host langue

+   - Specify the query in SQL as follows:

```
EXEC SQL
declare c cursor for
select ID, name
from student
where tot_cred > :credit_amount
END_EXEC
```

+   - The variable c (used in the cursor declaration) is used to identify the query
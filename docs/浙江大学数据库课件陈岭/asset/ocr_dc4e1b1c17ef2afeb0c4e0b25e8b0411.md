# # (1) The select Clause [Cont.]

+   - SQL allows duplicates in relations as well as in query results.

+   - To force the elimination of duplicates, insert the keyword distinct after select.

+   - Find the names of all branches in the loan relations, and remove duplicates

```
```sql
SELECT distinct branch_name
FROM loan
```
```

+   - The opposite keyword all allow duplicates.
+   select all branch_name from loan
+   By default, duplicates are allowed, i.t. ALL is the default
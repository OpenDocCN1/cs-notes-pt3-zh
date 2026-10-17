# Cascading Actions in SQL

```
create table *account*(

    ...

    foreign key(*branch-name*) references *branch*
        [ *on delete cascade* ]
        [ *on update cascade* ]
    ... );
```

+   - Due to the on delete cascade clauses, if a delete of a tuple in *branch* results in referential-integrity constraint violation, the delete “cascades” to the *account* relation, deleting the tuple in *account* that refers to the *branch* which was deleted.
+   - Cascading updates are similar.
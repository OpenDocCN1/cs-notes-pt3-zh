# Transaction Control in JDBC

By default, each SQL statement is treated as a separate transaction that is committed automatically

+   bad idea for transactions with multiple updates

Can turn off automatic commit on a connection

```
conn.setAutoCommit(false);
```

Transactions must then be committed or rolled back explicitly

+   conn.commit(); or

+   conn.rollback();

conn.setAutoCommit(true) turns on automatic commit.
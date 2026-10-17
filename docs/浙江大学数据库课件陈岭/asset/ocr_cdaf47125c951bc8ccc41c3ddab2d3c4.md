# Statement Level Triggers

Instead of executing a separate action for each affected row, a single action can be executed for all rows affected by a transaction.

+   - Use *for each statement* instead of *for each row*
+   - Use *referencing old table* or *referencing new table* to refer to temporary tables (called *transition tables*) containing the affected rows
+   - Can be more efficient when dealing with SQL statements that update a large number of rows.
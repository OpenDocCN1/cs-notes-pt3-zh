# LoadRunner——脚本录制与开发

# 关联

> You’ve reached this page incorrectly (probably a bad user session value). Please use this link.

```
lr_close_cursor(&csr10, 0);
lr_open_cursor(&csr11, Con1, 0);
lr_db_stmt("INSERT INTO Orders (order_number, agent_no, customer_no, flight_number, departure_date, tickets_ordered, class, send_signature with_order) VALUES (...)", -1, 1 /*Direct exec*/, 0 /*None*/, 0);
lr_close_cursor(&csr11, 0);
lr_commit(0, Con1, 0);
return 0;
```

```
vuser_init.c(78): lr_db_stmt: INSERT INTO Customers (customer_name, customer_no) VALUES ('AAA', 57)
vuser_init.c(82): lr_db_stmt: SELECT agent_no FROM Agents WHERE agent_name='Alex'
vuser_init.c(86): lr_db_fetch: 1 rows fetched
vuser_init.c(90): lr_db_stmt: SQLExecDirect, return_code=-1, native_error_code=-1605, SQLState=23000
vuser_init.c(94): lr_db_stmt: ERROR, return_code=LRD2009, INSERT INTO Orders (order_number, agent_no, customer_no, flight_number, ...)
Abort was called from an action.
```
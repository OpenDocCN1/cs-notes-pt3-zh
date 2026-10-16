![](bbox=[0.0, 0.0, 0.09, 0.14])

# User-Defined Types

+   create type construct in SQL creates user-defined type

```
create type Dollars as numeric (12,2) final
```

+   create table department
+   (dept_name varchar (20),
+   building varchar (15),
+   budget Dollars);
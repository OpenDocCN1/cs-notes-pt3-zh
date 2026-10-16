# Embedded SQL (Cont.)

Before executing any SQL statements, the program must first connect to the database. This is done using:

```
EXEC-SQL connect to server user user-name using password;
```

Here, server identifies the server to which a connection is to be established.

Variables of the host language can be used within embedded SQL statements. They are preceded by a colon (:) to distinguish from SQL variables (e.g., :credit_amount )

Variables used as above must be declared within DECLARE section, as illustrated below. The syntax for declaring the variables, however, follows the usual host language syntax.

```
EXEC-SQL BEGIN DECLARE SECTION
int credit-amount ;
EXEC-SQL END DECLARE SECTION;
```

![](bbox=[0.05, 0.02, 0.18, 0.1])
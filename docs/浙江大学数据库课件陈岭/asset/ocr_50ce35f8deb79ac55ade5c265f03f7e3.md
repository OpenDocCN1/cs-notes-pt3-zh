# [1] The select clause (Cont.)

+   - An asterisk `*` in the select clause denotes “all attributes”

```
SELECT * FROM loan;
```

+   - But, in the following example,

```
SELECT loan_number, branch_name,
amount * 100 FROM loan;
```

The select clause can contain **arithmetic expressions** involving the operation, `+`, `−`, `*`, and `/`, and operating on constants or attributes of tuples. (Generalized Projection)
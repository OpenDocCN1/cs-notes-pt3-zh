# # (2) The where Clause

The where clause specifies conditions that the result must satisfy, and it corresponds to the selection predicate of the relational algebra.

Π<sub>loan_number</sub>(σ<sub>branch_name='Perryridge'^ amount>1200</sub>(loan))

E.g: To find all loan number for loans made at the Perryridge branch with loan amounts greater than $1200.

```
```sql
SELECT loan_number
FROM loan
WHERE branch_name = 'Perryridge' and amount > 1200;
```
```

loan (loan-number, branch-name, amount)
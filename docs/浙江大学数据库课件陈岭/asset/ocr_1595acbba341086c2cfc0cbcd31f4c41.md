# # (2) The where Clause (Cont.)

- In WHERE clause comparison results can be combined using the logical connectives **AND**, **OR**, and **NOT**, and a **BETWEEN** comparison operator can be used for specifying a range.

+   - E.g. Find the loan number of those loans with loan amounts between $90,000 and $100,000 (that is, ≥$90,000 and ≤$100,000)

```
```sql
SELECT loan_number FROM loan
WHERE amount BETWEEN 90000 AND 100000;
```
```
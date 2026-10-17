# # View Example

Suppose a bank clerk needs to know the names of the customers of each branch, but is not authorized to see specific loan information.

+   - Approach: Deny direct access to the *loan* relation, but grant access to the view *cust-loan*, which consists only of the names of customers and the branches at which they have a loan.

+   - The *cust-loan* view is defined in SQL as follows:

```
```sql
create view cust-loan as
select branchname, customer-name
from borrower, loan
where borrower.loan-number = loan.loan-number;
```
```
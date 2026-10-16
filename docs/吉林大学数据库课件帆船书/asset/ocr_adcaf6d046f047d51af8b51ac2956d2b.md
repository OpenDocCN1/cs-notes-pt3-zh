# Windowing (Cont.)

+   Can do windowing within partitions

+   E.g., Given a relation transaction (account_number, date_time, value), where value is positive for a deposit and negative for a withdrawal

+   “Find total balance of each account after each transaction on the account”

```
select account_number, date_time,
  sum (value) over
    (partition by account_number
     order by date_time
     rows unbounded preceding)
  as balance
from transaction
order by account_number, date_time
```
# 3.9 (1) Deletion

Delete all **accounts** and relevant information at **depositor** for every branch located in Needham city.

```
DELETE FROM account
where branch_name in (select branch_name
from branch
where branch_city = 'Needham');
```

```
DELETE FROM depositor
where account_number in
(select account_number
from branch B, account A
where branch_city = 'Needham'
and B.branch_name = A.branch_name);
```
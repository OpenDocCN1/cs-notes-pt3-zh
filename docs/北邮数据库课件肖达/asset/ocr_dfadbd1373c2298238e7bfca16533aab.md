+   - *depositor* (customer-name, _account-number_)
+   - *borrower* (customer-name, _loan-number_)

+   - 找出在银行中同时有存款和贷款账户的客户

```
select  distinct customer-name
from    borrower
where   customer-name in
        (select customer-name
         from   depositor)
```

```
select  distinct customer-name
from    borrower
where   exists
        (select  *
         from    depositor
         where   depositor. customer-name
                 = borrower. customer-name)
```
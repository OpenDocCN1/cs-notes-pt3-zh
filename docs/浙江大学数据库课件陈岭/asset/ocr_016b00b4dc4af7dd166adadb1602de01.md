# Case Statement for Conditional Updates

Same query as before: Increase all accounts with balances over $10,000 by 6%; all other accounts receive 5%.

```
update account
   set balance = case
                  when balance <= 10000
                  then balance *1.05
                  else balance *1.06
                end;
```

This feature is supported by SQL Server 2000.
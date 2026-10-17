找出银行每个支行存款余额最大的帐号。

# ▪ Example 4: Find the account_number with maximum balance for every branch.

```
SELECT account_number FROM account
WHERE balance >= max(balance)
```

（X）

```
GROUP BY branch_name;
SELECT account_number, max(balance)
FROM account
GROUP BY branch_name;
```

（X）
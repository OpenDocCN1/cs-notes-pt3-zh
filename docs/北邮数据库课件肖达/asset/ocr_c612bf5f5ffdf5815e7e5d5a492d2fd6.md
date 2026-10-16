+   - *branch* (_branch-name_, branch-city, assets)
+   - *customer* (_customer-name_, customer-street, customer-city)
+   - *account* (_account-number_, branch-name, balance)
+   - *loan* (_loan-number_, branch-name, amount)
+   - *depositor* (customer-name, _account-number_)
+   - *borrower* (customer-name, _loan-number_)
+   - 找出在银行中同时有存款和贷款账户的客户（分别用IN和EXIST谓词完成）
+   - 找出那些总资产至少比位于Brooklyn 的某一家支行要多的支行名字（用ANY谓词完成）
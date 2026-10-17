# (1) XPath (Cont.)

+   - Attributes are accessed using “@”
+     - E.g:
+       `/bank-2/account[balance >400] /@account_number`
+         - returns the account numbers of accounts with balance > 400
+   - IDREF attributes are not dereferenced automatically (more on this later)
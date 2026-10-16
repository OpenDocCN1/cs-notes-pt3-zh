# 3NF Decomposition: An Example

+   - Relation schema:
+     *cust_banker_branch = (customer_id, employee_id, branch_name, type)*
+   - The functional dependencies for this relation schema are:
+     1. *customer_id, employee_id → branch_name, type*
+     2. *employee_id → branch_name*
+     3. *customer_id, branch_name → employee_id*
+   - We first compute a canonical cover
+     - *branch_name* is extraneous in the r.h.s. of the 1st dependency
+     - No other attribute is extraneous, so we get F_C =
+       *customer_id, employee_id → type*
+       *employee_id → branch_name*
+       *customer_id, branch_name → employee_id*
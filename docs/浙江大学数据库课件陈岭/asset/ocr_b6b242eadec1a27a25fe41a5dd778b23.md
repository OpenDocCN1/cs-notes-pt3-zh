# 🔺 Keys for Relationship Sets

+   - **The combination of primary keys of the participating entity sets forms a super key of a relationship set.**
+   
+     （参与一个联系集的各实体集的码的组合，构成该联系集的超码）
+   
+     - **(customer-id, loan-number)** is the **super key** of **borrower**
+     - **(s-id, c-id)** is the **super key** of **enrolled**
+     - **NOTE:** this means a pair of entity can have at most one relationship in a particular relationship set.

+   - **Must consider the mapping cardinality of the relationship set when deciding what are the candidate keys.** (1:1, 1:n, m:n)

+   - **Need to consider semantics of relationship set in selecting the primary key in case of more than one candidate key.**
+   
+     *e.g.*, 作为码的属性不能为空，值不应常变
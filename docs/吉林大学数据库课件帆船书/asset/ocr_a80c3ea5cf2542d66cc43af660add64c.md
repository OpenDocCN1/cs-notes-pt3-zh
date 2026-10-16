# APPLICATION-LEVEL AUTHORIZATION (CONT.)

+   - Currently, authorization is done entirely in application
+   - Entire application code has access to entire database
+     - large surface area, making protection harder
+   - Alternative: **fine-grained (row-level) authorization** schemes
+     - extensions to SQL authorization proposed but not currently implemented
+     - Oracle Virtual Private Database (VPD) allows predicates to be added transparently to all SQL queries, to enforce fine-grained authorization
+       - e.g. add *ID= sys_context.user_id()* to all queries on student relation if user is a student
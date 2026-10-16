# Path Expressions

+   - Find the names and addresses of the heads of all departments:
+     **select** head ->name, head ->address
+     **from** *departments*
+   - An expression such as “head->name” is called a **path expression**
+   - Path expressions help avoid explicit joins
+     - If department head were not a reference, a join of *departments* with *people* would be required to get at the address
+     - Makes expressing the query much easier for the user
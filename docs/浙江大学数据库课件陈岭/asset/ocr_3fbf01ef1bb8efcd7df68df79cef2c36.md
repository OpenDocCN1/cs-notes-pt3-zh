# (a) Privileges in SQL

+   - **select**: allows read access to relation, or the ability to query using the view
+   - **Example:** To grant users U₁, U₂, and U₃ select and insert authorization on the *branch* relation:
+     - SQL: `grant select, insert on branch to U₁, U₂, U₃;`
+   - **insert**: the ability to insert tuples
+   - **update**: the ability to update using the SQL update statement
+   - **delete**: the ability to delete tuples.
+   - **references**: ability to declare foreign keys when creating relations.
+   - **all privileges**: used as a short form for all the allowable privileges
+   - **all**
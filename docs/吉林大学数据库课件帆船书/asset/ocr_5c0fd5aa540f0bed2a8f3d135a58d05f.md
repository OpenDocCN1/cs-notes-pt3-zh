# Some Updates cannot be Translated Uniquely

+   - **create view** *instructor_info* **as**
+     **select** ID, name, building
+     **from** *instructor*, *department*
+     **where** *instructor.dept_name*= *department.dept_name*;
+   - **insert into** *instructor_info* **values** ('69987', 'White', 'Taylor');
+     - which department, if multiple departments in Taylor?
+     - what if no department is in Taylor?
+   - Most SQL implementations allow updates only on simple views
+     - The **from** clause has only one database relation.
+     - The **select** clause contains only attribute names of the relation, and does not have any expressions, aggregates, or **distinct** specification.
+     - Any attribute not listed in the **select** clause can be set to null
+     - The query does not have a **group** by or **having** clause.
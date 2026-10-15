# Representing Specialization as Schemas (Cont.)

+   - **Method 2:**
+     - Form a schema for each entity set with all local and inherited attributes
+   
+       | schema | attributes |
+       |---|---|
+       | person | ID, name, street, city |
+       | student | ID, name, street, city, tot_cred |
+       | employee | ID, name, street, city, salary |
+   
+     - If specialization is total, the schema for the generalized entity set (person) not required to store information
+     - Can be defined as a “view” relation containing union of specialization relations
+     - But explicit schema may still be needed for foreign key constraints
+     - Drawback: *name*, *street* and *city* may be stored redundantly for people who are both students and employees

| schema | attributes |
|---|---|
| person | ID, name, street, city |
| student | ID, name, street, city, tot_cred |
| employee | ID, name, street, city, salary |
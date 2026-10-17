# 7.7 Multivalued Dependencies

+   - There are database schemas in BCNF that do not seem to be sufficiently normalized.
+   - Consider a database

**classes(course, teacher, book)**  
we denote that **(c,t,b) ∈ classes** means that **t** is to teach **c**, and **b** is a required textbook for **c**.

+   - The database is supposed to list for each course the set of teachers *(any one of which can be the course’s instructor)*, and the set of books *(all of which are required for the course no matter who teaches it)*.

( **Course: teacher = 1:n**, **Course: book = 1:n**.  
**teacher** and **book** are multi-value attributes, and **teacher** and **book** are **independent**. )

![](bbox=[0.827, 0.775, 1.0, 1.0])

![](bbox=[0.0, 0.825, 0.062, 1.0])
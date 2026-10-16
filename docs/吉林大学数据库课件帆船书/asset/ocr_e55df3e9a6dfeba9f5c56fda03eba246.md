# Not Null and Unique Constraints

+   - **not null**
+     - Declare *name* and *budget* to be **not null**
+       *name* **varchar(20) not null**
+       *budget* **numeric(12,2) not null**

+   - **unique ( A₁, A₂, ..., Aₘ )**
+     - The unique specification states that the attributes A1, A2, ... Am form a candidate key.
+     - Candidate keys are permitted to be null (in contrast to primary keys).
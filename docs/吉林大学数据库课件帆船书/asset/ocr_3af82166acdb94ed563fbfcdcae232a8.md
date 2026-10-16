# Other Authorization Features

+   - **references** privilege to create foreign key
+     - **grant reference** (*dept_name*) **on** *department* **to** Mariano;
+     - why is this required?
+   - transfer of privileges
+     - **grant select on** *department* **to** Amit **with grant option**;
+     - **revoke select on** *department* **from** Amit, Satoshi **cascade**;
+     - **revoke select on** *department* **from** Amit, Satoshi **restrict**;
+   - Etc. read Section 4.6 for more details we have omitted here.
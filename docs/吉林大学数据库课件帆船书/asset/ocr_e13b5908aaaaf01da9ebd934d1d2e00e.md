# File Organization

![](bbox=[0.0, 0.02, 0.09, 0.14])

+   - The database is stored as a collection of *files*. Each file is a sequence of *records*. A record is a sequence of fields.
+   - One approach:
+     - assume record size is fixed
+     - each file has records of one particular type only
+     - different files are used for different relations
+   This case is easiest to implement; will consider variable length records later.
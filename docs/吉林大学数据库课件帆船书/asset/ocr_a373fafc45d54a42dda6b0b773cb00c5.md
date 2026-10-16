# SQL Injection

+   - Suppose query is constructed using
+     - "select * from instructor where name = '' + name + ''"

+   - Suppose the user, instead of entering a name, enters:
+     - X' or 'Y' = 'Y

+   - then the resulting statement becomes:
+     - "select * from instructor where name = '' + 'X' or 'Y' = 'Y' + ''"
+     - which is:
+       - select * from instructor where name = 'X' or 'Y' = 'Y'
+     - User could have even used
+       - X'; update instructor set salary = salary + 10000; --

+   - Prepared statement internally uses:
+     - "select * from instructor where name = 'X\' or \'Y\' = \'Y\'"

+   - Always use prepared statements, with user inputs as parameters

+   - Is the following prepared statemen secure?
+     - conn.prepareStatement("select * from instructor where name = '' + name + ''")

![](bbox=[0.0, 0.03, 0.12, 0.15])
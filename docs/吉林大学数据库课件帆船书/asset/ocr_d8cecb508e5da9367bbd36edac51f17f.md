# Deletion

+   - Delete all instructors
+     **delete from** *instructor*
+   - Delete all instructors from the Finance department
+     **delete from** *instructor*
+     **where** *dept_name*= 'Finance';
+   - Delete all tuples in the *instructor* relation for those instructors associated with a department located in the Watson building.
+     **delete from** *instructor*
+     **where** *dept name* in (**select** *dept name*
+     **from** *department*
+     **where** *building* = 'Watson');

![](bbox=[0.0, 0.03, 0.09, 0.14])
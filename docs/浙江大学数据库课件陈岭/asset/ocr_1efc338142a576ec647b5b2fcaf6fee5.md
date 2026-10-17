# Checking Referential Integrity on Database Modification (cont.)

**Delete.** If a tuple, $t_1$, is deleted from $r_1$, the system must compute the set of tuples in $r_2$ that reference $t_1$:

$$\sigma_\alpha = \{t[r_2]\}$$

> 如果r2中存在与r1中被删记录匹配的元组

If this set is **NOT** empty, then

+   - either the delete command is rejected as an error, or
+   - the tuples in $t_2$ that references $t_1$ **must themselves be deleted** (*cascading* (多级) deletions are possible).

![](bbox=[0.0, 0.0, 0.11, 0.115])

![](bbox=[0.82, 0.74, 1.0, 1.0])

![](bbox=[0.0, 0.83, 0.065, 1.0])
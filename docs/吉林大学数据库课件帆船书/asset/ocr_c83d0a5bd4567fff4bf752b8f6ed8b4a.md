# When Not To Use Triggers (Cont.)

![](bbox=[0.0, 0.0, 0.09, 0.13])

+   - Risk of unintended execution of triggers, for example, when
+     - Loading data from a backup copy
+     - Replicating updates at a remote site
+     - Trigger execution can be disabled before such actions.
+   - Other risks with triggers:
+     - Error leading to failure of critical transactions that set off the trigger
+     - Cascading execution
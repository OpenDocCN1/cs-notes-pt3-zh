# Detection-Algorithm Usage

+   - When, and how often, to invoke depends on:
+     - How often a deadlock is likely to occur?
+     - How many processes will be affected by deadlock when it happens?
+   - If detection algorithm is invoked arbitrarily, there may be many cycles in the resource graph and so we would not be able to tell which of the many deadlocked processes “caused” the deadlock.
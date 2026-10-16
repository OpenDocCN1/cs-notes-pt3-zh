# Dining Philosophers

+   - Each philosopher *i* invokes the operations **pickup()** and **putdown()** in the following sequence:
+     - dp.pickup (i)
+     - EAT
+     - dp.putdown (i)
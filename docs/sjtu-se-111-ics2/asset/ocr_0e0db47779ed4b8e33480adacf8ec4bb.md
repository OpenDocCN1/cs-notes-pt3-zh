# Branch Prediction (History) Buffer

+   - Problems with this simple scheme
+     - Does not do a good job of predicting “mostly-taken branches”
+       - `e.g., for (i=0; i<10; i++) { ... }`
+       - Repeated exec of the loop will result in **2 mispredictions**
+         - Last iteration flips T to NT
+         - First iteration flips NT to T
+       - Prediction accuracy of **80%**
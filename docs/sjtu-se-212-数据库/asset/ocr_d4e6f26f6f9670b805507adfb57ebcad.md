# Data Access (Cont.)

+   - Transactions
+     - Perform read(X) while accessing X for the first time;
+     - All subsequent accesses are to the local copy.
+     - After last access, transaction executes write(X).
+   - output(BX) need not immediately follow write(X). System can perform the output operation when it deems fit.
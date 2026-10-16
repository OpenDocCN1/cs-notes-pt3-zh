# Algorithm 1

+   - Shared variables:
+     - int turn;
+     initially turn = i (or turn=j)

+   - Process $P_i$:
+     do {  while (turn != i) ;
+     critical section
+     turn = j;
+     remainder section
+     } while (1);

+   - are forced to run in an alternating way.

+   - Satisfies mutual exclusion, but not progress
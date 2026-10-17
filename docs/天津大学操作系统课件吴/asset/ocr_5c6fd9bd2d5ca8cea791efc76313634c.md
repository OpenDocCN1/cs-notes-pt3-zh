# # Deadlock Detection with Multiple Resources of Each Type (2)

Deadlock detection algorithm:

+   1. Look for an unmarked process, _P<sub>i</sub>_, for which the i-th row of _R_ is less than or equal to _A_.

+   2. If such a process is found, add the _i-th_ row of _C_ to _A_, mark the process, and go back to step 1.

+   3. If no such process exists, the algorithm terminates.
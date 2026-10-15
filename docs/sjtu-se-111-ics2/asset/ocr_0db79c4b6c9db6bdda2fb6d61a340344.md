# Safe sharing with semaphores

Provide mutually exclusive access to shared variable by surrounding critical section with P and V operations on semaphore s (initially set to 1).

Semaphore invariant creates a forbidden region that encloses unsafe region and is never touched by any trajectory.

Initially
s = 1

![](bbox=[0.07, 0.24, 0.78, 0.84])
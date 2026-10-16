# List of Tasks Indexed According to Priorities

![](bbox=[0.18, 0.15, 0.68, 0.55])

+   - A runnable task is considered eligible for execution on the CPU as long as it has time remaining in its time slice.
+   - The kernel maintains a list of all runnable task in a runqueue data structure, each runqueue contains two priority arrays (see above fig.)
+   - Each processor maintains its own runqueue, schedules itself.
+   - When all task have exhausted their time slice, the two priority arrays are exchanged.
+   - The recalculation of a task’s dynamic priority occurs when the task has exhausted its time slice and is to be moved to the expired array.
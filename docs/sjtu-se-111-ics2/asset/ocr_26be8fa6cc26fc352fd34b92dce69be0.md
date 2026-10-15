# Using Semaphores to Schedule Access to Shared Resources

+   - _Basic idea_: Thread uses a semaphore operation to notify another thread that some condition has become true
+     - Use counting semaphores to keep track of resource state.
+     - Use binary semaphores to notify other threads.
+   - Two classic examples:
+     - The Producer-Consumer Problem
+     - The Readers-Writers Problem
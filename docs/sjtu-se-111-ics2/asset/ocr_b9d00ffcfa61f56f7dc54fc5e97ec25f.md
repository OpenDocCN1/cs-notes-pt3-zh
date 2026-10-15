# Thread-safe functions

+   - We identify four (non-disjoint) classes of thread-unsafe functions:
+     - Class 1: Failing to protect shared variables.
+     - Class 2: Relying on persistent state across invocations.
+     - Class 3: Returning a pointer to a static variable.
+     - Class 4: Calling thread-unsafe functions.
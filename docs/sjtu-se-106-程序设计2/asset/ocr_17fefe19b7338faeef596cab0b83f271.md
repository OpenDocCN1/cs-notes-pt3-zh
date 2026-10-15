# Introduction to Reference Counting

+   - Basic Problem
+     - Resource sharing is often more efficient than copying
+     - But it’s hard to tell when all are done using a resource
+     - Must avoid early deletion
+     - Must avoid leaks
+   - Solution Approach
+     - Share both the resource and also a counter
+     - Each new reference increments the counter
+     - When a reference is done, it decrements the counter
+     - When count drops to zero, delete resource and counter
+     - “last one out shuts off the lights”

![](bbox=[0.11, 0.28, 0.52, 0.71])
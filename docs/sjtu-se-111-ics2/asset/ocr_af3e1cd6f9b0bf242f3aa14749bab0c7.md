# Signaling with semaphores

![](bbox=[0.18, 0.26, 0.82, 0.44])

+   Common synchronization pattern:
+   - Producer waits for empty slot, inserts item in buffer, and notifies consumer
+   - Consumer waits for item, removes it from buffer, and notifies producer
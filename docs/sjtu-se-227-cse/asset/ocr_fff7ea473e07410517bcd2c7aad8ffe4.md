# Start the Scheduler

+   - Processor Thread
+     - Create a separate thread for each processor first
+     - Its stack is not used for most of the time
+       - Only used when running scheduler()
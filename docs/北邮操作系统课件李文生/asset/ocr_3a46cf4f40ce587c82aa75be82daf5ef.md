# 6.4 Synchronization Hardware

+   - Many systems provide hardware support for critical section code
+   - Uniprocessors – could disable interrupts
+     - Currently running code would execute without preemption
+     - Generally too inefficient on multiprocessor systems
+       - Operating systems using this not broadly scalable
+   - Modern machines provide special atomic hardware instructions
+     - Atomic = non-interruptible
+     - test memory word and set value
+     - swap contents of two memory words
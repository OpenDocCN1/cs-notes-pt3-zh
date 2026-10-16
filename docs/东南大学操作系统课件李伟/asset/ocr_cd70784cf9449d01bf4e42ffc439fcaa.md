# Windows XP Synchronization

+   - Uses **interrupt masks** (中断屏蔽) to protect access to global resources on uniprocessor systems.
+   - Uses *spinlocks* on multiprocessor systems.
+   - Also provides *dispatcher objects* which may act as mutex and semaphores.
+   - Dispatcher objects may also provide *events*. An event acts much like a condition variable.
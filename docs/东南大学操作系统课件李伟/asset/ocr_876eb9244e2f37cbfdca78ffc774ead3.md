# # Semaphore Implementation

+   - The main disadvantage of the above classical semaphore definition is that it requires **busy waiting**. *(while a process is in its critical section, any other process that tries to enter its critical section must loop continuously in the entry code)*
+   - This type of semaphore is also called a **spinlock (自旋锁)** because the process spins while waiting for the lock.
+   - To overcome the need for busy waiting, the process can **block itself** rather than engaging in busy waiting.
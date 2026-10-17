# # Monitor Implementation

+   - For each condition variable x, we have: semaphore x-sem; // (initially = 0) int x-count = 0;

+   - The operation x.wait can be implemented as:

```
x-count++;
if (next-count > 0)
    signal(next);
else
    signal(mutex);
wait(x-sem);
x-count--;
```
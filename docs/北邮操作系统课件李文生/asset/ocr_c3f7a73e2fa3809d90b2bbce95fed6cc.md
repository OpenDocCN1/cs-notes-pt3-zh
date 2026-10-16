# Mutual Exclusion with Swap

+   Shared data (initialized to false):
+   boolean lock;

+   Process P_i

```
do {
    key = true;
    while (key == TRUE)
        Swap (&lock, &key);
    critical section
    lock = FALSE;
    remainder section
} while(TRUE)
```

Mutual exclusion? √
Progress? √
Bounded-waiting? ×
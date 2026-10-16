# Initial Attempts to Solve Problem

+   - Only 2 processes, *P*₀ and *P*₁
+   - General structure of process *P*ᵢ (other process *P*ⱼ)

```
do {
    entry section
    critical section
    exit section
    remainder section
} while (1);
```

+   - Processes may share some common variables to synchronize their actions.
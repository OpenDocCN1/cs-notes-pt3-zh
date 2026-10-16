# Semaphore vs. Condition

| Semaphores | Condition Variables |
|---|---|
| Can be used anywhere, but not in a monitor | Can only be used in monitors |
| `wait()` does not always block its caller | `wait()` **always** blocks its caller |
| `signal()` either releases a process, or increases the semaphore counter | `signal()` either releases a process, or the signal is **lost** as if it never occurs |
| If `signal()` releases a process, the caller and the released **both continue** | If `signal()` releases a process, either the caller or the released continues, but **not both** |
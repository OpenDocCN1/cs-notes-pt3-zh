# Exceptions

| Class | Cause | Async/Sync | Return behavior |
|---|---|---|---|
| Interrupt | Signal from I/O device | Async | Always returns to next instruction |
| Trap | Intentional exception | Sync | Always returns to next instruction |
| Fault | Potentially recoverable error | Sync | Might return to current instruction |
| Abort | Nonrecoverable error | Sync | Never returns |

![](bbox=[0.04, 0.48, 0.48, 0.72])

![](bbox=[0.5, 0.48, 0.96, 0.72])

![](bbox=[0.04, 0.73, 0.48, 0.97])

![](bbox=[0.5, 0.73, 0.96, 0.97])
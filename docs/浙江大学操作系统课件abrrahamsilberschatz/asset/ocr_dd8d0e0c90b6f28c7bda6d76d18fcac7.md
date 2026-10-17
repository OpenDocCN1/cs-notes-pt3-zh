# # Monitor Implementation

+   - The operation x.signal can be implemented as:

```
if (x-count > 0) {
next-count++;
signal(x-sem);
wait(next);
next-count--;
}
```
# Lock Implementation (Incorrect)

```
structure lock {
    integer state;
}
void acquire (lock refrerence L) {
    while L.state = LOCKED {}      // spin until L is UNLOCKED
    L.state = LOCKED;              // the while test failed, got the lock
}
void release (lock reference L) {
    L.state = UNLOCKED;
}
```
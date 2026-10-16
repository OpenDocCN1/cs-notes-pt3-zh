# Supplement:
Implementing S as a Binary semaphore

# Wait(S) operation

```
wait (S1);
C--;
if (C < 0) {
    signal (S1);
    wait (S2)
}
else
    signal (S1);
```

# Signal(S) operation

```
wait (S1);
C ++;
if (C <= 0)
    signal(S2);
signal(S1);
```
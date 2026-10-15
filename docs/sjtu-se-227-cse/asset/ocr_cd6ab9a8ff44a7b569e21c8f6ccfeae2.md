# Review: Bounded Buffer Send/Receive

```
send(bb, m):
    while True:
        if bb.in − bb.out < N:
            bb.buff[bb.in mod N] ← m
            bb.in ← bb.in + 1
            return
```

```
receive(bb):
    while True:
        if bb.in > bb.out:
            m ← bb.buff[bb.out mod N]
            bb.out ← bb.out + 1
            return m
```

If the buffer is unavailable yet, wait by spinning
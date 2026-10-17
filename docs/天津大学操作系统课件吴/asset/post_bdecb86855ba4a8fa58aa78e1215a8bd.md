
Process A:

```
...
P(S);
Print(a.doc);
V(S);
...
```

Process B:

```
...
P(S);
Print(b.doc);
V(S);
...
```

Process C:

```
...
P(S);
Print(c.doc);
V(S);
...
```

P (Semaphore s){
    s=s-1;
    if (s<0){
        sleep...;
    }
}

V (Semaphore s){
    s=s+1;
    if (s<=0){
        wakeup...;
    }
}

- S = 1: Process A — Runnable
- S = 1 -> 0: Process A — Runnable
- S = 1 -> 0 -> -1: Process A — Runnable; Process B — Blocked; Process C — Runnable
- S = 1 -> 0 -> -1 -> -2: Process A — Runnable; Process B — Blocked; Process C — Blocked
- S = 1 -> 0 -> -1 -> -2 -> -1: Process A — Runnable; Process B — Runnable; Process C — Blocked
- S = 1 -> 0 -> -1 -> -2 -> -1 -> 0: Process A — Runnable; Process B — Runnable; Process C — Runnable
- S = 1 -> 0 -> -1 -> -2 -> -1 -> 0 -> 1: Process A — Runnable; Process B — Runnable; Process C — Runnable

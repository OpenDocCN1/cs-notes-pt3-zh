![](bbox=[0.012, 0.023, 0.262, 0.297])

S = 1 -> 0

Process A:
...
P(S);
Print(a.doc);
V(S);
... ...

Runnnable

```
```
P (Semaphore s){
    while (!s>0)
        yield;
    s--;
}
```
```

```
```
V (Semaphore s){
    s++;
}
```
```
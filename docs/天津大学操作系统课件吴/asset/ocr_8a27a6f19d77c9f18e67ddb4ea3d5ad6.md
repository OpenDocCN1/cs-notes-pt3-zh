# # Dining Philosophers Problem (4)

```
```c
void take_forks(int i)
{
    down(&mutex);
    state[i] = HUNGRY;
    test(i);
    up(&mutex);
    down(&s[i]);
}
```
```

A solution to the dining philosophers problem.
# Dining-Philosophers Problem

![](bbox=[0.04, 0.18, 0.38, 0.75])

Shared data
semaphore chopstick[5];
Initially all values are 1

# Philosopher i:

```
do{
    wait(chopstick[i]);
    wait(chopstick[(i+1) % 5]);
    ...
    eat
    ...
    signal(chopstick[i]);
    signal(chopstick[(i+1) % 5]);
    ...
    think
    ...
} while (1);
```
# Bounded-Buffer Problem
Producer Process

```
do {
    ...
        produce an item in nextp
        ...
        wait(empty);
        wait(mutex);
        ...
        add nextp to buffer
        ...
        signal(mutex);
        signal(full);
} while (1);
```
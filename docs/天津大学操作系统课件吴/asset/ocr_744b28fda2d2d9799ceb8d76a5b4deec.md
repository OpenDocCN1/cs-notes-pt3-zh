# Message Passing (3)

...

```
public synchronized int remove() {
    int val;
    if (count == 0) go_to_sleep();    // if the buffer is empty, go to sleep
    val = buffer [lo]; // fetch an item from the buffer
    lo = (lo + 1) % N;    // slot to fetch next item from
    count = count − 1;    // one few items in the buffer
    if (count == N − 1) notify(); // if producer was sleeping, wake it up
    return val;
}
private void go_to_sleep() { try{wait();} catch(InterruptedException exc) {};}
}
}
```

A solution to the producer-consumer
problem in Java.
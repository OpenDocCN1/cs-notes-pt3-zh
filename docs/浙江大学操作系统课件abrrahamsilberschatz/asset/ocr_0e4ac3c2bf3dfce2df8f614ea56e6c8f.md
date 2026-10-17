# Fig 7.22 A monitor solution to the Dining-\nPhilosophers (Cont.-1)

```
void test(int i) {
    if ( (state[(i + 4) % 5] != eating) &&
         (state[i] == hungry) &&
         (state[(i + 1) % 5] != eating)) {
        state[i] = eating;
        self[i].signal();
    }
}
```
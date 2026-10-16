# Algorithm 3 （Peterson Algorithm）

+   Combined shared variables of algorithms 1 and 2.

+   Process Pᵢ

```
do {
  flag [i]:= true;
  turn = j;
  while (flag [j] and turn = j) ;
  critical section
  flag [i] = false;
  remainder section
} while (1);
```

Mutual exclusion? √
Progress? √
Bounded-waiting? √

Solution for multiprocesses?
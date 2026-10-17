

## Deadlock Detection with Multiple Resources of Each Type (2)

Deadlock detection algorithm:

- 1. Look for an unmarked process, _P<sub>i</sub>_, for which the i-th row of _R_ is less than or equal to _A_.

- 2. If such a process is found, add the _i-th_ row of _C_ to _A_, mark the process, and go back to step 1.

- 3. If no such process exists, the algorithm terminates.

## Deadlock Detection with Multiple Resources of Each Type (3)

E = (4 2 3 1) A = (2 1 0 0)

Current allocation matrix

C = [
0 0 1 0
2 0 0 1
0 1 2 0
]

Request matrix

R = [
2 0 0 1
1 0 1 0
2 1 0 0
]

Figure 6-7. An example for the deadlock detection algorithm.

## Recovery from Deadlock

- Recovery through preemption
- Recovery through rollback
- Recovery through killing processes

## Safe and Unsafe States (1)

### (a)

|   | Has | Max |
|---|---:|---:|
| A | 3 | 9 |
| B | 2 | 4 |
| C | 2 | 7 |

Free: 3

### (b)

|   | Has | Max |
|---|---:|---:|
| A | 3 | 9 |
| B | 4 | 4 |
| C | 2 | 7 |

Free: 1

### (c)

|   | Has | Max |
|---|---:|---:|
| A | 3 | 9 |
| B | 0 | — |
| C | 2 | 7 |

Free: 5

### (d)

|   | Has | Max |
|---|---:|---:|
| A | 3 | 9 |
| B | 0 | — |
| C | 7 | 7 |

Free: 0

### (e)

|   | Has | Max |
|---|---:|---:|
| A | 3 | 9 |
| B | 0 | — |
| C | 0 | — |

Free: 7

Figure 6-9. Demonstration that the state in (a) is safe.

## The Banker's Algorithm for a Single Resource

Has Max

| A | 0 | 6 |
|---|---|---|
| B | 0 | 5 |
| C | 0 | 4 |
| D | 0 | 7 |

Free: 10

(a)

Has Max

| A | 1 | 6 |
|---|---|---|
| B | 1 | 5 |
| C | 2 | 4 |
| D | 4 | 7 |

Free: 2

(b)

Has Max

| A | 1 | 6 |
|---|---|---|
| B | 2 | 5 |
| C | 2 | 4 |
| D | 4 | 7 |

Free: 1

(c)

Figure 6-11. Three resource allocation states: (a) Safe. (b) Safe. (c) Unsafe.

## The Banker's Algorithm for Multiple Resources (1)

![](img/856cffd4f5aea27d2abb1fffe70c2f49_183_0.png)

![](img/856cffd4f5aea27d2abb1fffe70c2f49_183_1.png)

E = (6342)
P = (5322)
A = (1020)

Figure 6-12. The banker's algorithm with multiple resources.

## The Banker's Algorithm for Multiple Resources (2)

Algorithm for checking to see if a state is safe:

- 1. Look for row, R, whose unmet resource needs all ≤ A. If no such row exists, system will eventually deadlock since no process can run to completion

- 2. Assume process of row chosen requests all resources it needs and finishes. Mark process as terminated, add all its resources to the A vector.

- 3. Repeat steps 1 and 2 until either all processes marked terminated (initial state was safe) or no process left whose resource needs can be met (there is a deadlock).

## Deadlock Prevention

- Attacking the mutual exclusion condition
- Attacking the hold and wait condition
- Attacking the no preemption condition
- Attacking the circular wait condition

## Attacking the Circular Wait Condition

- 1. Imagesetter
- 2. Scanner
- 3. Plotter
- 4. Tape drive
- 5. CD-ROM drive

![](img/856cffd4f5aea27d2abb1fffe70c2f49_186_0.png)

(a)

(b)

Figure 6-13. (a) Numerically ordered resources.
(b) A resource graph.

## Approaches to Deadlock Prevention

| Condition | Approach |
|---|---|
| Mutual exclusion | Spool everything |
| Hold and wait | Request all resources initially |
| No preemption | Take resources away |
| Circular wait | Order resources numerically |

Figure 6-14. Summary of approaches to deadlock prevention.

## Other Issues

- Two-phase locking
- Communication deadlocks
- Livelock
- Starvation

## Communication Deadlocks

![](img/856cffd4f5aea27d2abb1fffe70c2f49_189_0.png)

Figure 6-15. A resource deadlock in a network.

## Livelock

```
void process_A(void) {
    enter_region(&resource_1);
    enter_region(&resource_2);
    use_both_resources();
    leave_region(&resource_2);
    leave_region(&resource_1);
}
```

```
void process_B(void) {
    enter_region(&resource_2);
    enter_region(&resource_1);
    use_both_resources();
    leave_region(&resource_1);
    leave_region(&resource_2);
}
```

Figure 6-16. Busy waiting that can lead to livelock.


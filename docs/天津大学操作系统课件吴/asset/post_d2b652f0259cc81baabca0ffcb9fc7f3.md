

## Resource Acquisition (2)

```c
typedef int semaphore;
semaphore resource_1;
semaphore resource_2;
void process_A(void) {
    down(&resource_1);
    down(&resource_2);
    use_both_resources();
    up(&resource_2);
    up(&resource_1);
}
void process_B(void) {
    down(&resource_1);
    down(&resource_2);
    use_both_resources();
    up(&resource_2);
    up(&resource_1);
}
```

Figure 6-2. (a) Deadlock-free code.

## Resource Acquisition (3)

```c
semaphore resource_1;
semaphore resource_2;

void process_A(void) {
    down(&resource_1);
    down(&resource_2);
    use_both_resources();
    up(&resource_2);
    up(&resource_1);
}

void process_B(void) {
    down(&resource_2);
    down(&resource_1);
    use_both_resources();
    up(&resource_1);
    up(&resource_2);
}
```

![](img/856cffd4f5aea27d2abb1fffe70c2f49_164_0.png)

## Introduction To Deadlocks

Deadlock can be defined formally as follows:

*A set of processes is deadlocked if each process in the set is waiting for an event that only another process in the set can cause.*

## Conditions for Resource Deadlocks

1. Mutual exclusion condition
2. Hold and wait condition.
3. No preemption condition.
4. Circular wait condition.

## Deadlock Modeling (2)

A
Request R
Request S
Release R
Release S
(a)

B
Request S
Request T
Release S
Release T
(b)

C
Request T
Request R
Release T
Release R
(c)

1. A requests R
2. B requests S
3. C requests T
4. A requests S
5. B requests T
6. C requests R
deadlock
(d)

![](img/856cffd4f5aea27d2abb1fffe70c2f49_168_0.png)

![](img/856cffd4f5aea27d2abb1fffe70c2f49_168_1.png)

![](img/856cffd4f5aea27d2abb1fffe70c2f49_168_2.png)

Figure 6-4. An example of how deadlock occurs and how it can be avoided.

## Deadlock Modeling (3)

1. A requests R
2. B requests S
3. C requests T
4. A requests S
5. B requests T
6. C requests R deadlock

![](img/856cffd4f5aea27d2abb1fffe70c2f49_169_0.png)

![](img/856cffd4f5aea27d2abb1fffe70c2f49_169_1.png)

![](img/856cffd4f5aea27d2abb1fffe70c2f49_169_2.png)

![](img/856cffd4f5aea27d2abb1fffe70c2f49_169_3.png)

![](img/856cffd4f5aea27d2abb1fffe70c2f49_169_4.png)

![](img/856cffd4f5aea27d2abb1fffe70c2f49_169_5.png)

Figure 6-4. An example of how deadlock occurs and how it can be avoided.

## Deadlock Modeling (5)

Strategies for dealing with deadlocks:

1. Just ignore the problem.
2. Detection and recovery. Let deadlocks occur, detect them, take action.
3. Dynamic avoidance by careful resource allocation.
4. Prevention, by structurally negating one of the four required conditions.

## Deadlock Detection with One Resource of Each Type (1)

![](img/856cffd4f5aea27d2abb1fffe70c2f49_172_0.png)

Figure 6-5. (a) A resource graph. (b) A cycle extracted from (a).

## Deadlock Detection with One Resource of Each Type (2)

Algorithm for detecting deadlock:

1. For each node, N in the graph, perform the following five steps with N as the starting node.
2. Initialize L to the empty list, designate all arcs as unmarked.
3. Add current node to end of L, check to see if node now appears in L two times. If it does, graph contains a cycle (listed in L), algorithm terminates.

## Deadlock Detection with One Resource of Each Type (3)

1. From given node, see if any unmarked outgoing arcs. If so, go to step 5; if not, go to step 6.
2. Pick an unmarked outgoing arc at random and mark it. Then follow it to the new current node and go to step 3.
3. If this is initial node, graph does not contain any cycles, algorithm terminates. Otherwise, dead end. Remove it, go back to previous node, make that one current node, go to step 3.

## Deadlock Detection with Multiple Resources of Each Type (1)

Resources in existence
(E1, E2, E3, ..., Em)

Resources available
(A1, A2, A3, ..., Am)

Current allocation matrix

| C11 | C12 | C13 | ... | C1m |
|-----|-----|-----|-----|-----|
| C21 | C22 | C23 | ... | C2m |
| ... | ... | ... | ... | ... |
| Cn1 | Cn2 | Cn3 | ... | Cnm |

Request matrix

| R11 | R12 | R13 | ... | R1m |
|-----|-----|-----|-----|-----|
| R21 | R22 | R23 | ... | R2m |
| ... | ... | ... | ... | ... |
| Rn1 | Rn2 | Rn3 | ... | Rnm |

Row n is current allocation to process n

Row 2 is what process 2 needs

Figure 6-6. The four data structures needed by the deadlock detection algorithm.


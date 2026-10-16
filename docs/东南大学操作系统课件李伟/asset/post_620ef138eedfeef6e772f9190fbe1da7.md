
## Outline

- Basic Concepts
- Scheduling Criteria
- Scheduling Algorithms
- Multiple-Processor Scheduling
- Real-Time Scheduling
- Thread Scheduling
- Algorithm Evaluation
- Operating System Examples

## Solaris 2 Scheduling

- Scheduling threads using preemptive and priority-based scheduling algorithms.
- The default scheduling class is time sharing —— Multilevel Feedback Queue

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_343_0.png)

### Solaris Dispatch Table

| priority | time quantum | time quantum expired | return from sleep |
|---:|---:|---:|---:|
| 0 | 200 | 0 | 50 |
| 5 | 200 | 0 | 50 |
| 10 | 160 | 0 | 51 |
| 15 | 160 | 5 | 51 |
| 20 | 120 | 10 | 52 |
| 25 | 120 | 15 | 52 |
| 30 | 80 | 20 | 53 |
| 35 | 80 | 25 | 54 |
| 40 | 40 | 30 | 55 |
| 45 | 40 | 35 | 56 |
| 50 | 40 | 40 | 58 |
| 55 | 40 | 45 | 58 |
| 59 | 20 | 49 | 59 |

## Windows XP Priorities

preemptive and priority-based scheduling algorithms

| | real-time | high | above normal | normal | below normal | idle priority |
|---|---|---|---|---|---|---|
| time-critical | 31 | 15 | 15 | 15 | 15 | 15 |
| highest | 26 | 15 | 12 | 10 | 8 | 6 |
| above normal | 25 | 14 | 11 | 9 | 7 | 5 |
| normal | 24 | 13 | 10 | 8 | 6 | 4 |
| below normal | 23 | 12 | 9 | 7 | 5 | 3 |
| lowest | 22 | 11 | 8 | 6 | 4 | 2 |
| idle | 16 | 1 | 1 | 1 | 1 | 1 |

## Linux Scheduling

- **preemptive** and **priority-based** scheduling algorithms
- Time-sharing
  - **Prioritized credit-based** – process with most credits is scheduled next
  - Credit subtracted when timer interrupt occurs
  - When credit = 0, another process chosen
  - When all runnable processes have credit = 0, recrediting occurs based on factors including priority and history

### The Relationship Between Priorities and Time-slice length

| numeric priority | relative priority | time quantum |
|---:|---|---|
| 0 | highest | 200 ms |
| • |  |  |
| • |  |  |
| • |  |  |
| 99 |  |  |
| 100 |  |  |
| • |  |  |
| • |  |  |
| • |  |  |
| 140 | lowest | 10 ms |

real-time tasks

other tasks

## 作业2

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_348_0.png)

- 课后习题5.4（P187）

## 操作系统原理及应用

李  伟

xchlw@seu.edu.cn

计算机科学与工程学院、软件学院
江苏省网络与信息安全重点实验室

## Chapter 6 Process Synchronization

### Outline

- Background
- The Critical-Section Problem
- Synchronization Hardware
- Semaphores
- Classical Problems of Synchronization
- Monitors
- Synchronization Examples

### Background

- Concurrent access to shared data may result in data inconsistency.
- Maintaining data consistency requires mechanisms to ensure the orderly execution of cooperating processes.
- Shared-memory solution to **bounded-buffer problem** (Chapter 3) allows at most *n* − 1 items in buffer at the same time.
- Suppose that we wanted to provide a solution to the consumer-producer problem that fills **all** the buffers.
  - We can do so by having an integer **count** that keeps track of the number of full buffers

### Bounded-Buffer

- Shared data

```
#define BUFFER_SIZE 10
typedef struct {
    ...
} item;
item buffer[BUFFER_SIZE];
int in = 0;
int out = 0;
int counter = 0;
```

- Producer process

```
item nextProduced;
while (1) {
    while (counter == BUFFER_SIZE);
        /* do nothing */
    buffer[in] = nextProduced;
    in = (in + 1) % BUFFER_SIZE;
    counter++;
}
```

- **Consumer process**

```
item nextConsumed;
while (1) {
    while (counter == 0);
        /* do nothing */
    nextConsumed = buffer[out];
    out = (out + 1) % BUFFER_SIZE;
    counter--;
}
```

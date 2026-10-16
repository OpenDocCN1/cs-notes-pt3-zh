
## Convoy(护航) effect

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_325_0.png)

## 5.3.2 Shortest-Job-First (SJF) Scheduling

- SJF algorithm associates with each process the length of its next CPU burst. Use these lengths to schedule the process with the shortest time.
- Two schemes:
  - **nonpreemptive** – once CPU is given to the process, it cannot be preempted until it completes its CPU burst.
  - **preemptive** – if a new process arrives with CPU burst length less than remaining time of current executing process, preempt. This scheme is known as the **Shortest-Remaining-Time-First (SRTF)**.
- SJF is optimal – gives minimum average waiting time for a given set of processes.

### Example of Non-Preemptive SJF

| Process | Arrival Time | Burst Time |
|---|---|---|
| P₁ | 0 | 7 |
| P₂ | 2 | 4 |
| P₃ | 4 | 1 |
| P₄ | 5 | 4 |

SJF (non-preemptive)

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_327_0.png)

Waiting time for P₁=0; P₂=6; P₃=3; P₄=7

Average waiting time = (0 + 6 + 3 + 7)/4 = 4

### SJF

| Process | Arrival Time | Burst |
|---|---|---|
| P₁ | 0 | 7 |
| P₂ | 2 | 4 |
| P₃ | 4 | 1 |
| P₄ | 5 | 4 |

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_328_0.png)

Waiting time for P₁=0; P₂=6; P₃=3; P₄=7

turnaround time P₁=7; P₂=10; P₃=4; P₄=11

### Example of Preemptive SJF

| Process | Arrival Time | Burst Time |
|---|---|---|
| P₁ | 0 | 7 |
| P₂ | 2 | 4 |
| P₃ | 4 | 1 |
| P₄ | 5 | 4 |

SRTF (preemptive SJF)

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_329_0.png)

P₂ arrives
P₁: 5, P₂: 4

P₃ arrives
P₂: 2, P₃: 1

P₄ arrives
P₁: 5, P₂: 2, P₄: 4

- Wait time for P₁=9; P₂=1; P₃=0; P₄=2
- Average waiting time = (9 + 1 + 0 + 2)/4 = 3

### SRTF

| Process | Arrival Time | Burst |
|---|---|---|
| P₁ | 0 | 7 |
| P₂ | 2 | 4 |
| P₃ | 4 | 1 |
| P₄ | 5 | 4 |

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_330_0.png)

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_330_1.png)

- Waiting time for P₁=9; P₂=1; P₃=0; P₄=2
- turnaround time P₁=16; P₂=5; P₃=1; P₄=6

### Prediction of the Length of the Next CPU Burst (*)

- Can only estimate the length.
- Can be done by using the length of previous CPU bursts, using exponential averaging.
  - tₙ = actual length of nth CPU burst
  - τₙ₊₁ = predicted value for the next CPU burst
  - α, 0 ≤ α ≤ 1
  - define:
    
    τₙ₊₁ = α tₙ + (1 − α) τₙ

τₙ₊₁ = α tₙ + (1-α)α tₙ₋₁ + ... + (1-α)ʲ α tₙ₋ⱼ + ... + (1-α)ⁿ⁺¹ τ₀

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_332_0.png)

$\tau_{n+1}=\alpha\hat{t}_n+(1-\alpha)\tau_n\qquad \alpha=1/2\qquad \tau_0=10$

|  |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|
| **CPU burst** ($t_i$) | 6 | 4 | 6 | 4 | 13 | 13 | 13 |  |
| **“guess”** ($\tau_i$) | 10 | 8 | 6 | 6 | 5 | 9 | 11 | 12 |

### Examples of Exponential Averaging

τₙ₊₁ = α tₙ + (1 − α) τₙ

- α = 0
  - τₙ₊₁ = τₙ  Recent history does not count.
- α = 1
  - τₙ₊₁ = tₙ  Only the actual last CPU burst counts.
- If we expand the formula, we get:
  
  τₙ₊₁ = α tₙ + (1−α) α tₙ₋₁ + ... + (1−α)ʲ α tₙ₋ⱼ + ... + (1−α)ⁿ⁺¹ τ₀
- Since both α and (1−α) are less than or equal to 1, each successive term has less weight than its predecessor.

## 5.3.3 Priority Scheduling

- A priority number (integer) is associated with each process
- The CPU is allocated to the process with the highest priority (smallest integer = highest priority).
- Equal-priority processes are scheduled in FCFS order.
- Two schemes:
  - **Preemptive**: preempt the CPU if the priority of the newly arrived process is higher than the priority of the currently running process.
  - **Nonpreemptive**: simply put the new process at the head of the ready queue.
- Priority can be defined either internally or externally.

- SJF is a priority scheduling where priority is the predicted next CPU burst time.
- Problem: Starvation (or indefinite blocking)—low priority processes may never execute.
- Solution: Aging – as time progresses increase the priority of the process.
- For example
  - If priorities range from 127 (low) to 0 (high)
  - We could decrease the priority number of a waiting process by 1 every 15 minutes.
  - Eventually, even a process with an initial priority of 127 would have the highest priority in the system and would be executed.

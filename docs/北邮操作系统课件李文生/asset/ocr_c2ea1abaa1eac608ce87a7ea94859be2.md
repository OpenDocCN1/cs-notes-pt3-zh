# 5. Considering a real-time system, in which there are 4 real-time processes P1, P2, P3 and P4 that are aimed to react to 4 critical environmental events e1, e2, e3 and e4 in time respectively.

The arrival time of each event ei, 1≤i≤4, (that is, the arrival time of the process Pi), the length of the CPU burst time of each process Pi, and the deadline for each event ei are given below. Here, the deadline for ei is defined as the absolute time point before which the process Pi must be completed.

The priority for each event ei (also for Pi) is also given, and a smaller priority number implies a higher priority.

| Events | Process | Arrival Time | Burst Time | Priorities | Deadline |
|---|---|---|---|---|---|
| e1 | P1 | 0.00 | 4.00 | 3 | 7.00 |
| e2 | P2 | 3.00 | 2.00 | 1 | 5.50 |
| e3 | P3 | 4.00 | 2.00 | 4 | 12.01 |
| e4 | P4 | 6.00 | 4.00 | 2 | 11.00 |

# (1) Suppose that priority-based preemptive scheduling is employed

Draw a Gantt chart illustrating the execution of these processes.
What are the average waiting time and the average turnaround time.
Which event will be treated with in time, that is, the process reacting to this event will be completed before its deadline?

# (2) Suppose that FCFS scheduling is employed

Draw a Gantt chart illustrating the execution of these processes.
What are the average waiting time and the average turnaround time.
Which event will be treated with in time?
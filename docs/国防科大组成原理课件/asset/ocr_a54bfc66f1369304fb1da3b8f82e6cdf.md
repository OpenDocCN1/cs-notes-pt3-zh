# perf stat

+   - perf stat ls Makefile（执行的程序为： “ls Makefile”）

Makefile

Performance counter stats for 'ls Makefile':

```
2.204554 task-clock-msecs   # 0.842 CPUs
0 context-switches  # 0.000 M/sec
0 CPU-migrations    # 0.000 M/sec
240 page-faults     # 0.109 M/sec
2176584 cycles      # 987.313 M/sec
1224357 instructions    # 0.563 IPC
60577 cache-references  # 27.478 M/sec
1788 cache-misses   # 0.811 M/sec
```

0.002618700 seconds time elapsed
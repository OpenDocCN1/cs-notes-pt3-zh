# # Round Robin (Cont.)

+   - Performance 特性
+     - \( q \ large \Rightarrow \text{FIFO} \)
+     - \( q \ small \Rightarrow q \text{ must be large with respect to context switch, otherwise overhead is too high.} \)
+     - \( q \)相对于切换上下文的时间而言不许足够长，否则将导致系统开销过大
# Schedulers (Cont.)

+   - **Short-term scheduler** is invoked very frequently (milliseconds) ⇒ (must be fast). 短程调度切换频率高

+   - **Long-term scheduler** is invoked very infrequently (seconds, minutes) ⇒ (may be slow). 长程调度不快

+   - The long-term scheduler controls the *degree of multiprogramming*. 长程调度控制了多道程序的“道”

+   - Processes can be described as either:
+   
+     进程可以用下列方式描述：
+   
+     - *I/O-bound process* – spends more time doing I/O than computations, many short CPU bursts.
+   
+       I/O型进程 - 花费I/O时间多于计算，许多短CPU处理
+   
+     - *CPU-bound process* – spends more time doing computations; few very long CPU bursts.
+   
+       CPU 型进程 - 花费更多时间于计算，许多长CPU处理
# 4.2.3 Context Switch
上下文切换

+   - When CPU switches to another process, the system must save the state of the old process and load the saved state for the new process.
+     当CPU切换至另一个进程时，系统必须保存旧进程状态并为新进程调入所保留的状态
+   - Context-switch time is overhead; the system does no useful work while switching.
+     上下文切换的时间开销较重；在切换时，系统没有做有用的工作
+   - Time dependent on hardware support.
+     时间取决于硬件的支持
# 异步异常 Asynchronous Exceptions (中断 Interrupts)

+   - 处理器外部I/O设备引起
+     - 由处理器的中断引脚指示
+     - 中断处理程序返回到下一条指令处

+   - Examples:
+     - 时钟中断(Timer interrupt)
+     - 定时器芯片每隔几毫秒触发一次中断
+     - 内核从用户程序取回控制权

+   - 外部设备的I/O中断(I/O interrupt from external device)
+     - 键盘上敲击一个 Ctrl-C
+     - 网络数据包到达
+     - 磁盘数据的到达

![](bbox=[0.48, 0.2, 1.0, 0.58])
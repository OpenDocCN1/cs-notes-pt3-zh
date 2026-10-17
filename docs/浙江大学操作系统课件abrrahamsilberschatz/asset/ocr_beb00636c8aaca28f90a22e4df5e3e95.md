# # I/O Structure (Cont.)

+   Asynchronous I/O: After I/O starts, control returns to user program without waiting for I/O completion.

异步I/O ： 在I/O开始之后， 不等I/O完成控制就返回用户程序

+   System call – request to the operating system to allow user to wait for I/O completion.

系统调用一请求操作系统允许用户等待I/O完成

+   Device-status table – contains entry for each I/O device indicating its type, address, and state.

设备状态表一包括每个I/O设备的类型、 地址和状态

+   Operating system first determines which I/O device caused the interrupt. It then indexes into I/O device table to determine device status and to modify table entry to reflect the occurrencen of the interrupt.

操作系统首先确定哪个I/O设备发出中断，然后引用设备状态表以确定设备状态并修改表入口以响应中断发生。
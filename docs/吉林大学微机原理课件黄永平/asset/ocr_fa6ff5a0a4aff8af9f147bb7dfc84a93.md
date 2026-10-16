# 任务状态段TSS

HYPer

| 31 ... 16 15 ... 2 1 0 |
|---|---|
| 返回链 |
| ESP0 |  |
| SS0 |  |
| ESP1 |  |
| SS1 |  |
| ESP2 |  |
| SS2 |  |
| CR3 |  |
| EIP |  |
| EFLAGS |  |
| EAX |  |
| ECX |  |
| EDX |  |
| EBX |  |
| ESP |  |
| EBP |  |
| ESI |  |
| EDI |  |
| ES |  |
| CS |  |
| SS |  |
| DS |  |
| FS |  |
| GS |  |
| LDT选择符 |  |
| I/O位图偏移地址 | T |
| 系统状态缓冲区(OS用) |  |
| I/O许可位图 |  |

前一个任务选择符

CPL0,1,2 的堆栈

前一个状态页目录寄存器

寄存器 的基地址

当前任务状态

简图

TSS
LDT选择符

GDT
LDT描述符
基址

LDT
描述符

GDT
LDT描述符
基址
LDT
描述符

调试用
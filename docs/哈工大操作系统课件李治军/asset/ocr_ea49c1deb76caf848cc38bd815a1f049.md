# 计算机硬件、操作系统、启动、接口...

温故： 设备管理的表格进行了初始化；等待用户的设备使用(系统调用)，将其展开成设备细节

```
void main(void)
{  mem_init();
    trap_init();
    .....
    sched_init();
    buffer_init();
    hd_init();
    floppy_init();
    sti();
    move_to_user_mode();
    if(!fork()){init();}
}
```

![](bbox=[0.48, 0.33, 0.78, 0.62])
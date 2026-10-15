# Timer Interrupt

```
49 switch(tf->trapno){
50 case T_IRQ0 + IRQ_TIMER:
51     if(cpu->id == 0){
52         acquire(&tickslock);
53         ticks++;
54         wakeup(&ticks);
55         release(&tickslock);
56     }
57     lapiceoi();
58 break;
```

```
58 int
59 sys_sleep(void)
60 {
61     int n;
62     uint ticks0;
63     if(argint(0, &n) < 0)
64         return -1;
65     acquire(&tickslock);
66     ticks0 = ticks;
67     while(ticks - ticks0 < n){
68         if(proc->killed){
69             release(&tickslock);
70             return -1;
71         }
72         sleep(&ticks, &tickslock);
73     }
74     release(&tickslock);
75     return 0;
77 }
```
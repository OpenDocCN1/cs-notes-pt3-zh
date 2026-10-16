# counter的作用: 时间片

```
void do_timer(...)  //在kernel/sched.c中
{  if((--current->counter>0) return;
   current->counter=0;
   schedule(); }
```

```
_timer_interrupt: //在kernel/system_call.s中
    call _do_timer
```

```
void sched_init(void) {
    set_intr_gate(0x20, &timer_interrupt);
```

counter是典型的时间片，所以是轮转调度，保证了响应

![](bbox=[0.92, 0.72, 0.98, 0.92])
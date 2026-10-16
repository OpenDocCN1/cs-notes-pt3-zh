# 开始copy_process

```
copy_process(...long eip, ...){
    p = (PCB *)get_free_page();
    p -> tss.esp0 = p+4k;
    p -> tss.esp = esp;
    p -> tss.eax=0; p -> tss.eip = eip;...}
```

![](bbox=[0.122, 0.539, 0.707, 0.878])
# 一个实际系统的请求调页

+   这个故事从哪里开始？

+   请求调页，当然从缺页中断开始

| 中断号 | 名称 | 说明 |
|---|---|---|
| 12 | Segment not Present | 描述符所指的段不存在 |
| 14 | Page fault | 页不在内存 |

```
void trap_init(void)
{ set_trap_gate(14, &page_fault); }
```

```
#define set_trap_gate(n, addr) \
_set_gate(&idt[n], 15, 0, addr);
```

![](bbox=[0.9, 0.76, 0.985, 0.91])
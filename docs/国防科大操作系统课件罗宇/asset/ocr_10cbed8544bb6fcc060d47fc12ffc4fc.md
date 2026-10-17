# irqaction结构记录当中断发生时具体的处理函数

```
struct irqaction {
    void (*handler)(int, void *, struct pt_regs *);    /*具体的处理函数*/
    unsigned long flags;
    unsigned long mask;
    const char *name;
    void *dev_id;
    struct irqaction *next; /*利用该成员形成链表*/
};
```

irq_desc_t 的 action 成员实际是一个 irqaction 结构的链表，因为多个设备可能共享一个中断源，每个设备都必须提供一个 irqction 结构挂入 action 链表。
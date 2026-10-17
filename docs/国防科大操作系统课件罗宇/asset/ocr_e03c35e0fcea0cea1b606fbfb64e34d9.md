对于8259A芯片来讲，它的具体成员如下：

```
static struct hw_interrupt_type i8259A_irq_type =
{
    "XT-PIC",
    startup_8259A_irq,
    shutdown_8259A_irq,
    enable_8259A_irq,
    disable_8259A_irq,
    mask_and_ack_8259A,
    end_8259A_irq,
    NULL
};
typedef struct hw_interrupt_type hw_irq_controller;
```
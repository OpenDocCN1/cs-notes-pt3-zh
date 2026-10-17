# 首条指令

+   - 初始化CPO（0号协处理器，用于控制处理器行为）
+     - 状态寄存器Status
+     - 原因寄存器Cause
+   - 初始化软件约定使用的通用寄存器
+     - 栈指针：BIOS用的堆栈
+     - 全局指针：BIOS用的地址空间
+     - 内核约定物理地址240MB-256MB之间的空间给BIOS用

```
mtc0    zero, COP_0_STATUS_REG        mtc0    zero,c0_sr
mtc0    zero, COP_0_CAUSE_REG         mtc0    zero,c0_cause
li      t0, SR_BOOT_EXC_VEC           lui     t0,0x40
mtc0    t0, COP_0_STATUS_REG          mtc0    t0,c0_sr
la      sp, stack                    lui     sp,0x8f90
la      gp, _gp                      addiu   sp,sp,-16384
                                      lui     gp,0x8f9a
                                      addiu   gp,gp,-8192
```
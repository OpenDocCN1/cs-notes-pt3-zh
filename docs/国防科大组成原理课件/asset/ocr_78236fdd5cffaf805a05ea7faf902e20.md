# 原子操作指令

+   - 以MIPS的LL和SC指令 为例
+     - LL(Load Linked)取数且置系统中LLbit为1
+     - LL为1时，处理器检查相应单元是否被修改，如果其它处理器或设备访问了相应单元或执行了ERET操作，LLbit置为0
+     - 执行SC（Store Conditional）时若LLbit为1，则成功，目标寄存器为1；否则存数不成功，目标寄存器为0

```
L1: LL    R1,(R3)
    ADD   R2,R1,1
    SC    R2,(R3)
    BEQ   R2,0,L1
    NOP
```
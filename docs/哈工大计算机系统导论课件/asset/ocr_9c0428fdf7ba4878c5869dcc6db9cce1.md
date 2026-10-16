# 读内存

| 访问 | 指令 | 说明 |
|---|---|---|
| 访问 | OPq rA, rB | 无操作 |
| 访问 | rmmovq rA, D(rB) | M₈[valE] ← valA | 数据写入内存 |
| 访问 | popq rA | valM ← M₈[valA] | 从栈里读取数据 |
| 访问 | jXX Dest | 无操作 |
| 访问 | call Dest | M₈[valE] ← valIP | 返回值入栈 |
| 访问 | ret | valM ← M₈[valA] | 读返回地址 |

```
bool mem_read = icode in { IMRMOVQ, IPOPQ, IRET };
```
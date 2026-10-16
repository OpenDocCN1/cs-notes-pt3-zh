# # 完整的内存寻址模式

# ■ 一般形式： D(Rb,Ri,S)

含义：Mem[Reg[Rb]+S*Reg[Ri]+D]

索引化的寻址方式

+   - D——常量，表示位移量(displacement): 1, 2, or 4 字节
+   - Rb——基址寄存器(Base register): 所有16位整数寄存器
+   - Ri——变址寄存器(Index register): 不可用%rsp
+   - S——比例因子(Scale): 1, 2, 4, or 8 *(why these numbers?)*

# ■ 特殊情况

| 地址形式 | 有效地址 |
|---|---|
| (Rb,Ri) | Mem[Reg[Rb]+Reg[Ri]] |
| D(Rb,Ri) | Mem[Reg[Rb]+Reg[Ri]+D] |
| (Rb,Ri,S) | Mem[Reg[Rb]+S*Reg[Ri]] |
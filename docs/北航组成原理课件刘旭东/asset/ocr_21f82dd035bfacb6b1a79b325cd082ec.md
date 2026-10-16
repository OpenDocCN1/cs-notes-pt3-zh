# 2.3 数据通路设计（10. 外部总线接口）

![](bbox=[0.011, 0.118, 0.973, 0.949])

控制总线（CB）

数据总线（DB）

地址总线（AB）

内部总线（IB）

CPU内部

MAR

MDR

| AH | AL |
|---|---|
| BH | BL |
| CH | CL |
| DH | DL |
| SP |   |
| BP |   |
| SI |   |
| DI |   |

ALU

PC

IR

存储器

> ◆ IB与AB之间：
> 地址驱动，加入MAR
> IB→MAR，MAR→AB
> 
> ◆ IB与DB之间：
> 数据缓存，加入MDR
> IB→MDR，MDR→DB
> DB→MDR，MDR→IB
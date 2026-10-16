# 距离向量路由算法：举例

node x table

| cost to | x | y | z |
|---|---|---|---|
| from x | 0 | 2 | 7 |
| y | ∞ | ∞ | ∞ |
| z | ∞ | ∞ | ∞ |

node y table

| cost to | x | y | z |
|---|---|---|---|
| from x | ∞ | ∞ | ∞ |
| y | 2 | 0 | 1 |
| z | ∞ | ∞ | ∞ |

node z table

| cost to | x | y | z |
|---|---|---|---|
| from x | ∞ | ∞ | ∞ |
| y | ∞ | ∞ | ∞ |
| z | 7 | 1 | 0 |

| cost to | x | y | z |
|---|---|---|---|
| from x | 0 | 2 | 3 |
| y | 2 | 0 | 1 |
| z | 7 | 1 | 0 |

Dx(y) = min{c(x,y) + Dy(y), c(x,z) + Dz(y)} = min{2+0 , 7+1} = 2

Dx(z) = min{c(x,y) + Dy(z), c(x,z) + Dz(z)} = min{2+1 , 7+0} = 3

![](bbox=[0.77, 0.4, 0.97, 0.6])
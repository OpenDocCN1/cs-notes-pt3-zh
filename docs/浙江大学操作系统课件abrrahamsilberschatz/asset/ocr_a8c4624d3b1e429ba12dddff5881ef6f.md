# Fig9.8 Paging Example for a 32-byte memory
with 4-byte pages

![](bbox=[0.231, 0.146, 0.779, 0.954])

| 逻辑地址 | 内容 |
|---:|:---|
| 0 | a |
| 1 | b |
| 2 | c |
| 3 | d |
| 4 | e |
| 5 | f |
| 6 | g |
| 7 | h |
| 8 | i |
| 9 | j |
| 10 | k |
| 11 | l |
| 12 | m |
| 13 | n |
| 14 | o |
| 15 | p |

logical memory

| 页号 | 页框号 |
|---:|---:|
| 0 | 5 |
| 1 | 6 |
| 2 | 1 |
| 3 | 2 |

page table

| 物理地址 | 内容 |
|---:|:---|
| 0 |  |
| 4 | i, j, k |
| 8 | m, n, o, p |
| 12 |  |
| 16 |  |
| 20 | a, b, c, d |
| 24 | e, f, g, h |
| 28 |  |

physical memory
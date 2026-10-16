# 2.2 线性表的存储结构---静态链表（Cont.）

操作的实现--- ②可用空间的分配操作

```
Cursor GetNode() //q=new spacestr;
{
    Cursor p;
    if (SPACE[avail].next ==-1)
        p=-1;
    else {
        p= SPACE[avail].next ;
        SPACE[avail].next =
            SPACE[ p ].next ;
    }
    return p;
} /*从存储池SPACE中删除结点*/
```

|   | data | next |
|---|------|------|
| 0 | d    | 6    |
| 1 |      | 5    |
| 2 | c    | -1   |
| 3 | /--/ | 0    |
| 4 | a    | 10   |
| 5 |      | 8    |
| 6 | e    | -1   |
| 7 | /--/ | 4    |
| 8 |      | -1   |
| 9 | /--/ | 11   |
| 10| b    | 2    |
| 11|      | 12   |
| 12|      | 1    |
SPACE

L=7
M=3
avail=9
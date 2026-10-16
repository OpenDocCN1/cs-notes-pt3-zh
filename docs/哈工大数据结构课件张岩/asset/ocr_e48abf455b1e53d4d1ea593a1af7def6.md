# 2.2线性表的存储结构---顺序表（Cont.）

```
① void Insert ( ElemType x, position p, LIST &L)
{ position q ;
    if (L.last >= Max - 1)
        cout<< " 表满 ";
    else if (( p > L.last +1 ) || ( p < 1 ))
        cout<< " 指定位置不存在 ";
    else {
        for ( q = L.last; q >= p; q -- )
            L.elements[ q+1 ] = L.elements[ q ];
        L.elements[ p ] = x ;
        L.last = L.last + 1 ;
    }
}
```

| | |
|---|---| 
| 0 | //// |
| 1 | a₁ |
| 2 | a₂ |
|  | .... |
|  |  |
| i | aᵢ |
|  | .... |
|  |  |
| last | aₙ |
|  |  |
| max-1 |  |
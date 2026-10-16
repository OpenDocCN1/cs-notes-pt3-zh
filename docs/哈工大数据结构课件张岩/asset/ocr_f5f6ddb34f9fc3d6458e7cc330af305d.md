# 2.2线性表的存储结构---顺序表（Cont.）

其他操作的实现

```
position Locate ( Elementtype x , LIST L ) //②
{ position q ;
    for ( q = 1; q <= L.last ; q++ )
        if ( L.elements[ q ] == x )
            return ( q );
    return ( L.last + 1 );
} //时间复杂度： O(n)
```

```
ElemType Retrieve ( position p , LIST L ) //③
{ if ( p > L.last )
    cout<< "指定元素不存在" ;
  else
    return ( L.elements[ p ] );
} //时间复杂度： O(1)
```

![](bbox=[0.88, 0.25, 0.98, 0.92])
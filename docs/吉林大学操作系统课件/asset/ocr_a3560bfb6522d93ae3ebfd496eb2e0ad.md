```
}else{
    if (a+size == bp->m_addr && bp->m_size) {  //与后合
        bp->m_addr -= size;
        bp->m_size += size;
    } else if (size) do {  //无合并
        t = bp->m_addr;
        bp->m_addr = a;
        a = t;  //a与bp->m_addr交换
        t = bp->m_size;
        bp->m_size = size;
        bp++;  //size与bp->m_size交换
    }while (size = t);
}
}
```
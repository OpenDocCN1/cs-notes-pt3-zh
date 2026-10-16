```
pt sort(pt base ) {        /* 链表排序，base 为链首 */
    pt p ,p0 ,r ,r0 ,q ;
    p0 = NULL ;
    p = base ;
    while ( p!=NULL ) {  /* 逐项处理，把p加入到子序列中，并保持 “base--p”递增 */
        r = base ;      /* 寻找位置 */
        while ( ( r->key < p->key ) && ( r!=p ) ) {
            r0 = r ;
            r = r-> next ;
        }
        if (r!=p) {  /* p插入到r0、r之间 */ /* 若 r==p ，在链尾，则不用插入 */
            q = p ;      /* 把 p 独立出来，令 q 指向它 */
            p0->next = p->next ;
            p = p0 ;
            if ( r == base ) {      /* 插入 */      /* 插在链首 */
                q->next = base ;
                base = q ;
            } else {      /* 插在链中r0、r之间 */
                q->next = r ;
                r0 -> next = q ;
            }
        }
        p0 = p ;      /* 前进一项 */
        p = p->next ;
    }
    return base ;
} /* sort */
```
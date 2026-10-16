程序如下：

```
void adds( int exp0 , float coef0 , polynome r ) {
    /* 向s加入一项 */
    polynome r0;
    r0 = ( polynome)malloc( sizeof(struct item) );
    r0->exp = exp0;
    r0->coef = coef0;
    r0->next = NULL;
    r->next=r0;
}
```
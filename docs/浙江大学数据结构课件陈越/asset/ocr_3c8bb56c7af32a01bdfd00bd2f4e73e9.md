```
void Attach( int c, int e, Polynomial *pRear )
{
    /* 由于在本函数中需要改变当前结果表达式尾项指针的值， */
    /* 所以函数传递进来的是结点指针的地址，*pRear指向尾项*/
    Polynomial P;

    P =(Polynomial)malloc(sizeof(struct PolyNode)); /* 申请新结点 */
    P->coef = c;    /* 对新结点赋值 */
    P->expon = e;
    P->link=NULL;
    /* 将P指向的新结点插入到当前结果表达式尾项的后面 */
    (*pRear)->link = P;
    *pRear = P;   /* 修改pRear值 */
}
```

![](bbox=[0.197, 0.632, 0.753, 0.855])
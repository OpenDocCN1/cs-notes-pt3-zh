如下实现栈的操作：

```
void stackinitial(void) {
    top = NULL ;
}
void stackpush ( items x ) {
    pstacktype  p ;
    p = (pstacktype)malloc(sizeof(stackcelltype));
    p->data = x ;
    p->prodocessor = top ;
    top = p ;
}
void stackpop ( items *x ) {
    pstacktype p ;
    if ( top != NULL ) {
        *x = top->data ;
        p = top ;
        top = top->predecessor ;
        free(p);
    } else printf( "栈下溢\n" );
}
```
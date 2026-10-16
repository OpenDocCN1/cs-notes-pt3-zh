```
treepointer del( treepointer * , treepointer * ); /* 处理第三种情况的函数的函数原型 */
void deletenode( keytype c , treepointer *p ) { /* 删除关键字值等于 c 的结点 */
    treepointer r;
    if ( *p == NULL )
        printf( "not found:%d\n" , c );
    else if ( c < (*p) -> key )
        /* c< 当前结点的 key 值，被删结点在左子树上 */
        deletenode( c , &((*p) -> left) );
    else if ( c > (*p) -> key )
        /* c> 当前结点的 key 值，被删结点在右子树上 */
        deletenode( c , &((*p) -> right) );
```
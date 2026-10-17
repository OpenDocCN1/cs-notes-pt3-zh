# # 顺序表基本运算

# ## 初始化

```
void InitList ( SeqList & L ) {
L.data = ( ListData * ) malloc
( ListSize * sizeof ( ListData ) );
if ( L.data == NULL ) {
printf ( "存储分配失败!\n" );
exit (1);
}
L.length = 0;
}
```
# ◆ 如何快速计算：

h("abcde")='a'*324+'b'*323+'c'*322+'d'*32+'e'

```
Index Hash ( const char *Key, int TableSize )
{
    unsigned int h = 0;    /* 散列函数值，初始化为0 */
    while ( *Key != '\0' )  /* 位移映射 */
        h = ( h << 5 ) + *Key++;
    return h % TableSize;
}
```
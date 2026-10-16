```
```c
int A[9];
bool check(); /* 检查某格局是否合格的函数, 分程序略 */
void out(); /* 输出函数, 分程序略 */
void queen( int r ) {
int i;
for ( i=1; i<=8; i++ ) {
A[8-r+1]=i;
if ( r>0 )
queen(r-1);
else if ( check() )
out();
}
}
int main(void) {
queen(8)
}
```
```
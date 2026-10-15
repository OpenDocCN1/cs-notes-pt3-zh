# 重载与域

```
namespace libs_R_us {
    int max( int, int );
    int max( double, double );
    extern void print( int );
    extern void print( double );
}
// using 声明
using libs_R_us::max;
using libs_R_us::print( double ); // 错误
void func()
{
    max( 87, 65 ); // 调用 libs_R_us::max( int, int )
    max( 35.5, 76.6 ); // 调用 libs_R_us::max( double, double )
}
```
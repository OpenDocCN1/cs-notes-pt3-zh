# 通过宏来得到具体的取值范围！

```
#include <limits.h>
```

| char | int | short | long | long long |
| SCHAR_MIN | INT_MAX | SHRT_MAX | LONG_MAX | LLONG_MAX |
| SCHAR_MAX | INT_MIN | SHRT_MIN | LONG_MIN | LLONG_MIN |
| UCHAR_MAX | UINT_MAX | USHRT_MAX | ULONG_MAX | ULLONG_MAX |
| CHAR_MIN |  |  |  |  |
| CHAR_MAX |  |  |  |  |

char类型有符号/无符号 由编译器决定
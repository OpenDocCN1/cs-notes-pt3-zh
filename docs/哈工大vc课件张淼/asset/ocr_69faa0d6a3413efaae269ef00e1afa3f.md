# 引用示例

# 定义引用并使用引用

```
```cpp
#include <iostream>
using namespace std;

void main()
{
    int a = 50;
    int& b = a;
    a = 100;
    cout << "a=" << a << endl;
    cout << "b=" << b << endl;
}
```
```
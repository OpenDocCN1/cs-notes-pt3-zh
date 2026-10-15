# 引用类型

```
```cpp
• Example: references
int ival = 1024;
int &refVal = &ival;       // 错误，refVal 是int 类型，不是int*
int *pi = &ival;
int *&ptrVal2 = pi;        // ok: refPtr 是一个指向指针的引用

int min_val = 0;
refVal = min_val;          // ival 被设置为min_val的值
                           // refVal 并没有引用到min_val 上
refVal += 2;

int ii = refVal;           // 把与 ival 相关联的值赋给 ii
int *pi = &refVal;         // 用ival 的地址初始化pi
```
```
# 函数重载解析

+   - 函数重载解析的过程有三个步骤

```
void f();
void f( int );
void f( double, double = 3.4 );
void f( char*, char* );
int main() {
    f( 5.6 );
    return 0;
}
```

+   - 确定函数调用考虑的重载函数的集合，确定函数调用中实参表的属性
+   - 候选集合
+   - f()
+   - f(int)
+   - f(double, double)
+   - f(char*, char*)
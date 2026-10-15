# 声明与定义

+   - 不能对同一事物定义两次
+     - 定义是在说明这是什么事物
+     - 例如

```
int a;        // definition
int a;        // error: double definition
double sqrt(double d) { ... }        // definition
double sqrt(double d) { ... }        // error: double definition
```

+   - 可以对同一事物声明两次
+     - 声明是在说明事物可以如何使用

```
int a = 7;        // definition (also a declaration)
extern int a;        // declaration
double sqrt(double);        // declaration
double sqrt(double d) { ... }        // definition (also a declaration)
```
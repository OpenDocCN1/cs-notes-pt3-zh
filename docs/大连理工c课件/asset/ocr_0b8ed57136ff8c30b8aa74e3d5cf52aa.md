# 9.3 流操作

# 9.3.1 格式化输入输出

在基类ios中定义了相关的控制符和成员函数在头文件iomanip中还声明了一些普通函数

| 控制符 | 成员函数 | 作用 |
|---|---|---|
| setfill(char c) | fill(char c) | 设置填充字符为字符常量或字符变量c |
| setprecision(int n) | precision(int n) | 设置显示小数的精度为n位 |
| setw(int n) | width(int n) | 设置域宽为n个字符 |
| setiosflags() | setf() | 设置输出格式的状态 |
| resetiosflags() | unsetf() | 清除已设置输出格式 |
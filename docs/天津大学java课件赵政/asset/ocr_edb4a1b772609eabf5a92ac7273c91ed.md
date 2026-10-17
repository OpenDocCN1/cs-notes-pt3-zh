# 5.1.2 switch语句

+   - 基于一个表达式的值来使程序执行不同部分的简单方法。
+   - 通用形式如下：

```
switch (expression) {    // exp 必须为 byte，short，int 或 char 类型
    case value1:          // value 必须是与表达式类型兼容的常量
        // statement sequence
        break;    // 当遇break时，程序将从switch后的第一行代码开始继续执行
    case value2:
        // statement sequence
        break;
    .
    .
    case valueN:
        // statement sequence
        break;
    default://若无case常量与值相匹配，则执行default语句。default是可选。
    // default statement sequence
}
```


- Programming I
- *程序设计 I*

感谢！

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_538_0.png)

## 程序设计 I

程序设计 I

## 第十四章
完成程序

第十四章

## 完成程序

翻译自 Bjarne Stroustrup 的课件

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_539_0.png)

- 输入和输出
- 错误处理
- 负数
- 取余 %
- 清理代码
  - 提示符
  - 程序组织
    - 常量
  - 从错误中恢复
  - 编写注释
  - 代码复审
  - 测试
- 复杂性和难易性讨论
  - 变量

- 我们可以不断地完善它
  - 风格——代码的清晰度
    - 注释
    - 命名
    - 函数的使用
    - ...
  - 功能——它能做什么
    - 更好的提示符
    - 从错误中恢复
    - 负数
    - %（取余）
    - 预定义表征值
    - 变量
    - ...

为什么没有采用下面的方式：
表达式：
结果：

表达式：2+3；5*7；2+9；
结果：5
表达式：结果：35
表达式：结果：11
表达式：

为什么采用了下面的方式：
2+3;
=5

5*7;
=35

2+3; 5*7; 2+9;
=5
=35
= 11

## 增加输入提示符和输出指示符

```
double val = 0;
cout << "> ";                         // print prompt
while (cin) {
    Token t = ts.get();
    if (t.kind == 'q') break;              // check for “quit”
    if (t.kind == ';')
        cout << "=" << val << "\n> ";    // print “= result” and prompt
    else
        ts.putback(t);
    val = expression();                    // read and evaluate expression
}
```

```
> 2+3; 5*7; 2+9;  //the program doesn’t see input before you hit “enter/return”
= 5
> = 35
> = 11
>
```

## 错误处理

- ➢ 反复测试程序

```
catch (exception& e) {
    cerr << e.what() << endl;
    keep_window_open();
    return 1;
}
```

- ➢ 可以使程序在捕获异常之后继续保持窗口打开

我们的计算机还不支持负数运算

- -1+2

初级表达式：
  数字
  "(" 表达式 ")"

修改为：

初级表达式：
  数字
  "(" 表达式 ")"
  "-" 初级表达式
  "+" 初级表达式

## 负数

```
double primary()
{ Token t = ts.get();
  switch (t.kind) {
  case '(':        // handle '(' expression ')'
    { double d = expression();
      t = ts.get();
      if (t.kind != ')') error("')' expected");
      return d;
    }
  case '8':        // we use '8' to represent a number
    return t.value;  // return the number's value
  case '-':
    return - primary();
  case '+':
    return primary();
  default:
    error("primary expected");
  }
}
```

- 将 % 添加到 Token 集合中
- 将 `double` 转型为 `int`，以支持 %

```
case '%':
{
    double d = term();
    int i1 = int(left);
    if (i1 != left) error ("left-hand operand of % not int");
    int i2 = int(d);
    if (i2 != d) error ("right-hand operand of % not int");
    if (i2 == 0) error("%: divide by zero");
    left = i1%i2;
    t = ts.get();
    break;
}
```

## 代码开始变得杂乱

- Bug 在杂乱的角落中茁壮成长
- 是时候清理代码了！
  - 仔细通读所有代码
    - 尽量系统化（“是否看过所有代码？”）
  - 改善注释
  - 将含混的名字替换为更好的名字
  - 改善函数的使用
    - 增加函数以简化杂乱的代码
  - 移除“魔幻常量”
    - 例如 ‘8’（‘8’ 表示什么？为什么是 8？）
- 一旦完成清理，让朋友或同事复审代码（“代码复审”）

```
// In Token_stream::get():

case '.':
case '0': case '1': case '2': case '3': case '4':
case '5': case '6': case '7': case '8': case '9':
  { cin.putback(ch);        // put digit back into the input stream
    double val;
    cin >> val;             // read a floating-point number
    return Token(number,val); // rather than Token('8',val)
  }

// In primary():

case number: // rather than case '8':
  return t.value;   // return the number's value

```
// In main():

while (cin) {
    cout << prompt;        // rather than "> "
    Token t = ts.get();
    while (t.kind == print) t=ts.get();    // rather than ==';'
    if (t.kind == quit) {    // rather than == 'q'
        keep_window_open();
        return 0;
    }
    ts.putback(t);
    cout << result << expression() << endl;
}
```

## 移除魔幻常量

- 但是，“魔幻常量”有什么错呢？
  - 每个人都知道 3.14159265358979323846264、12、-1、365、24、2.7182818284590、299792458、2.54、1.61、-273.15、6.6260693e-34、0.5291772108e-10、6.0221415e23 和 42！
  - 不，当然不是
- “魔幻”对身心健康不利！
  - 让你没完没了地熬夜找 Bug
  - 让你走向自我否定和自我毁灭
- 如果一个“常量”可能发生变化（在程序维护期间），或者某人不认识它，那么就使用表征常量
  - 精度变化是经常遇到的一种变化：3.14 != 3.14159265
  - 0 和 1 通常不需要解释，但是 -1 和 2 就需要解释
  - 12 可能可行（一年中月份的数量），但也可能不行（参见第 10 章）。
- 如果某个常量会用到多次，那么它就应该是表征常量
  - 这样我们就只需要在一个地方进行修改


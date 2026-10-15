
## 移除魔幻常量

- 关键问题是
  - 现在你已经看到了我们前面的代码是多么丑陋
    - 回去看看吧
  - 因为我们忘记了，所以编写了这样的代码
    - “清理代码”是非常重要的活动
      - 不只针对学生
      - 当你做出修改之后，一定要再次测试
    - 我们应该经常先停止增加新功能，返回去复审代码
      - 这样更节约时间

## 使用函数

- 通过使用函数，使每个函数职责都更加明晰

```
void calculate()  // expression evaluation loop
{
    while (cin) {
        cout << prompt;
        Token t = ts.get();
        while (t.kind == print) t=ts.get(); // first discard all "prints"
        if (t.kind == quit) return;      // quit
        ts.putback(t);
        cout << result << expression() << endl;
    }
}
```

```
int main()
try {
    calculate();
    keep_window_open();  // cope with Windows console mode
    return 0;
}
catch (runtime_error& e) {
    cerr << e.what() << endl;
    keep_window_open("~~");
    return 1; }
catch (...) {
    cerr << "exception \n";
    keep_window_open("~~");
    return 2; }
```

```
switch (ch) {
    case quit:
    case print:
    case '(':
    case ')':
    case '+':
    case '-':
    case '*':
    case '/':
    case '%':
        return Token(ch); // let each character represent itself
    case '.':      // a floating-point literal can start with a dot
```

## 代码外观布局

```
case '0': case '1': case '2': case '3': case '4':
case '5': case '6': case '7': case '8': case '9':  // numeric literal
{
    cin.putback(ch); // put digit back into the input stream
    double val;
    cin >> val;  // read a floating-point number
    return Token(number,val); // "a number"
}
default:
    error("Bad token");
}
}
```

```
/* Simple calculator
Revision history:
    Revised by Bjarne Stroustrup May 2007
    Revised by Bjarne Stroustrup August 2006
    Revised by Bjarne Stroustrup August 2004
    Originally written by Bjarne Stroustrup
      (bs@cs.tamu.edu) Spring 2004.
This program implements a basic expression calculator.
Input from cin; output to cout.
The grammar for input is:
    Statement:
      Expression
      ......
Input comes from cin through the Token_stream called ts.
*/

## 从错误中恢复

- 任何用户错误都会终止程序
  - 这并不理想
  - 代码结构

```
int main()
try {
  // ... do "everything" ...
}
catch (exception& e) {  // catch errors we understand something about
  // ...
}
catch(...) {  // catch all other errors
  // ...
}
```

- 将计算任务从main()中分离
  - main() 只执行初始化和清理

```
int main()    // step 1
try {
    calculate();
    keep_window_open();        // cope with Windows console mode
    return 0;
}
catch (exception& e) {        // errors we understand something about
    cerr << e.what() << endl;
    keep_window_open("~~");
    return 1;
}
catch (...) {                 // other errors
    cerr << "exception \n";
    keep_window_open("~~");
    return 2;
}
```

- 将读入和计算循环放入calculate() 中，可以简化代码

```
void calculate()
{
    while (cin) {
        cout << prompt;
        Token t = ts.get();
        while (t.kind == print) t=ts.get();    // first discard all "prints"
        if (t.kind == quit) return;            // quit
        ts.putback(t);
        cout << result << expression() << endl;
    }
}
```

- 将处理异常的代码从error() 移入calculate()

```
int main()    // step 2
try {
    calculate();
    keep_window_open();    // cope with Windows console mode
    return 0;
}
catch (...) {    // other errors (don’t try to recover)
    cerr << "exception \n";
    keep_window_open("~~");
    return 2;
}
```

```
void calculate()
{
    while (cin)
    try {
        cout << prompt;
        Token t = ts.get();
        while (t.kind == print) t=ts.get();    // first discard all "prints"
        if (t.kind == quit) return;            // quit
        ts.putback(t);
        cout << result << expression() << endl;
    }
    catch (exception& e) {
        cerr << e.what() << endl;             // write error message
        clean_up_mess();                      // <<< The tricky part!
    }
}
```

- 第一次尝试

```
void clean_up_mess()
{
    while (true) {        // skip until we find a print
        Token t = ts.get();
        if (t.kind == print) return;
    }
}
```

- 但是，这不能很好地工作。为什么？

- 考虑输入为：1@$z; 1+3;

- 当因为碰到了@而调用clean_up_mess()时，会调用get，此时得到$，再次是一个“Bad token”，于是错误抛给了main，程序终止

- 在处理错误的代码中不能产生新的错误

# 符号流

```
switch (ch) {
case ';':  // 用于"打印"
case 'q':  // 用于"退出"
case '(': case ')': case '+': case '-': case '*': case '/':
    return Token(ch);      // 每个字符表示自身
case '.':
case '0': case '1': case '2': case '3': case '4':
case '5': case '6': case '7': case '8': case '9':
{ cin.putback(ch);    // 将数字放回到输入流中
    double val;
    cin >> val;         // 读入一个浮点数
    return Token('8',val); // 用'8'表示"数字"
}
default: error("Bad token");
}
}
```


## 追踪优先级解析器

```
int main() {
Expression *readE(TokenScanner & scanner, int prec) {
Expression *exp = readT(scanner);
string token;
while (true) {
token = scanner.nextToken();
int newPrec = precedence(token);
if (newPrec <= prec) break;
Expression *rhs = readE(scanner, newPrec);
exp = new CompoundExp(token, exp, rhs);
}
scanner.saveToken(token);
return exp;
}
}
```

| scanner | prec | newPrec | token | exp | rhs |
| odd = 2 * n + 1 | 1 | 0 |  | • | • |

![](img/af430dff16b82a0fe61ce7dee05dcf9c_485_0.png)

## 追踪优先级解析器

```
int main() {
Expression *readE(TokenScanner & scanner, int prec) {
    Expression *exp = readT(scanner);
    string token;
    while (true) {
        token = scanner.nextToken();
        int newPrec = precedence(token);
        if (newPrec <= prec) break;
        Expression *rhs = readE(scanner, newPrec);
        exp = new CompoundExp(token, exp, rhs);
    }
    scanner.saveToken(token);
    return exp;
}
}
```

![](img/af430dff16b82a0fe61ce7dee05dcf9c_486_0.png)

## 追踪优先级解析器

```
int main() {
    Expression *readE(TokenScanner & scanner, int prec) {
        Expression *exp = readT(scanner);
        string token;
        while (true) {
            token = scanner.nextToken();
            int newPrec = precedence(token);
            if (newPrec <= prec) break;
            Expression *rhs = readE(scanner, newPrec);
            exp = new CompoundExp(token, exp, rhs);
        }
        scanner.saveToken(token);
        return exp;
    }
}
```

| scanner | prec | newPrec | token | exp | rhs |
|---|---|---|---|---|---|
| odd = 2 * n + 1 | 0 | 0 |  | • | • |

## 追踪优先级解析器

```
int main() {
    TokenScanner scanner = new TokenScanner();
    scanner.setInput("odd = 2 * n + 1");
    scanner.ignoreWhitespace();
    Expression *exp = readE(scanner);
    ...
}
```

scanner
odd = 2 * n + 1
^

exp

![](img/af430dff16b82a0fe61ce7dee05dcf9c_489_0.png)

## 基础入门项目

## Starter 文件夹中的模块

Basic.cpp
你来写这个，但它很短。

exp.h
exp.cpp
你不需要修改这些。

evalstate.h
evalstate.cpp
你需要做一个小的扩展。

parser.h
parser.cpp
你需要移除 = 运算符。

program.h
programpriv.h
program.cpp
你被提供了接口，但需要同时设计数据结构和实现。

statement.h
statement.cpp
你被提供了接口，需要提供实现。

## 语句类层次结构

- 学生需要构建一个语句形式层次结构，其结构与表达式类平行：

![](img/af430dff16b82a0fe61ce7dee05dcf9c_492_0.png)

```
#include <iostream>
#include "exp.h"
#include "map.h"
#include "parser.h"
#include "simpio.h"
#include "tokenscanner.h"

/* Function prototypes */
string convertToRPN(Expression *exp);

/* Main program */
int main() {
    cout << "This program converts expressions to RPN." << endl;
    TokenScanner scanner;
    scanner.ignoreWhitespace();
    scanner.scanNumbers();
    while (true) {
        cout << ">> ";
        string line = getLine();
        if (line == "quit") break;
        scanner.setInput(line);
        Expression *exp = parseExp(scanner);
        cout << convertToRPN(exp) << endl;
    }
    return 0;
}
```

## 示例

- 编写一个简化正则表达式的解析器
- 在字母表 [a-z] 上，简化正则表达式比普通正则表达式简单得多。
- 它只有两个元字符：'.' 和 '*'。
- '.' -- 精确匹配一个任意字符。
- '*' -- 匹配零个或多个任意字符。

## 结束

## 二叉搜索树

## 郑伟 齐

大部分幻灯片来自 Eric Roberts，CS 106B，斯坦福大学


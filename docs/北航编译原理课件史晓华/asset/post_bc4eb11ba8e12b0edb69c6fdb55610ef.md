
## Compiler

```text
<语句>::= <变量> := <表达式>
         | IF <表达式> THEN <语句> [ELSE <语句>]

<变量>::= i['<表达式>']

<表达式>::= <项>{+<项>}

<项>::= <因子>{*<因子>}

<因子>::= <变量> | '(' <表达式> ')'
```

```pascal
PROCEDURE term;                    /*项*/
BEGIN
    factor;
    WHILE sym='*' DO
        BEGIN nextsym; factor END
END;
```

```pascal
PROCEDURE factor;                  /*因子*/
BEGIN
    IF sym='(' THEN
        BEGIN nextsym; expr;
            IF sym <> ')' THEN error
            ELSE nextsym
        END
    ELSE var;
END
```

```c
void statement()
{
    if (sym == "if") {
        getsym();
        expr();
        if (sym != "then")
            error();
        else {
            getsym();
            statement();
            if (sym == "else") {
                getsym();
                statement();
            }
        }
    }
    else {
        var();
        if (sym != ":=")
            error();
        else {
            getsym();
            expr();
        }
    }
}
```

```c
void var()
{
    if (sym != "i") error();
    else {
        getsym();
        if (sym == "[") {
            getsym();
            expr();
            if (sym != "]")
                error();
            else getsym();
        }
    }
}
```

```c
void expr()
{
    term();
    while (sym == "+") {
        getsym();
        term();
    }
}
```

```c
void term()
{
    factor();
    while (sym == "*") {
        getsym();
        factor();
    }
}
```

```c
void main()
{
    getsym();
    statement();
}
```

```c
void factor()
{
    if (sym == "(") {
        getsym();
        expr();
        if (sym != ")") error();
        else getsym();
    }
    else var();
}
```

```c
void error()
{
    printf("syntax error !\n");
}
```

## 举例分析

```text
if (i+i) then i:=i*i+i else
  i[i] := i+i[i*i]*(i+i)
```

作业：

p90: 1-3

## Compiler

```text
<语句>::= <变量> := <表达式>
         | IF <表达式> THEN <语句> [ELSE <语句>]

<变量>::= i['<表达式>']

<表达式>::= <项>{+<项>}

<项>::= <因子>{*<因子>}

<因子>::= <变量> | '(' <表达式> ')'
```

```c
void statement()
{
    if (sym == "if") {
        getsym();
        expr();
        if (sym != "then")
            error();
        else {
            getsym();
            statement();
            if (sym == "else") {
                getsym();
                statement();
            }
        }
    }
    printf(" it is a statement \n");
    ...
}
```

```c
void var()
{
    if (sym != "i") error();
    else {
        getsym();
        if (sym == "[") {
            getsym();
            expr();
            if (sym != "]")
                error();
            else getsym();
        }
    }
}
```

```c
void expr()
{
    term();
    while (sym == "+") {
        getsym();
        term();
    }
}
```

```c
printf(" it is a statement \n");
printf(" it is a variable \n");
printf(" it is a expression \n");
```

```c
void term()
{
    factor();
    while (sym == "*") {
        getsym();
        factor();
    }
}
```

```c
void main()
{
    getsym();
    statement();
}
```

```c
void factor()
{
    if (sym == "(") {
        getsym();
        expr();
        if (sym != ")") error();
        else getsym();
    }
    else var();
}
```

```c
void error()
{
    printf("syntax error !\n");
}
```

```c
printf(" it is a term \n");
printf(" it is a factor \n");
```

## 4.2.5 LL分析法

LL—自左向右扫描、自左向右地分析和匹配输入串。
∴ 分析过程表现为最左推导的性质。

### 1、LL分析程序构造及分析过程

由三部分组成：

- 分析表
- 执行程序（总控程序）
- 符号栈（分析栈）

![](img/1ebd4dbc150db02388404d0c659c1fd7_257_0.png)

在实际语言中，每一种语法成分都有确定的左右界符，为了研究问题方便，统一以‘#’表示。

![](img/1ebd4dbc150db02388404d0c659c1fd7_258_0.png)

### （1）分析表：二维矩阵 M

M[A,a] = { A::=αi 或 error }   αi ∈ V*   A ∈ Vn   a ∈ Vt or #

M[A,a] = A::=αi

表示当要用A去匹配输入串时，且当前输入符号为a时，可用A的第i个选择去匹配。
即 当αi≠ε时，有αi⇒a...；
当αi=ε时，则a为A的后继符号。

M[A,a] = error

表示当用A去匹配输入串时，若当前输入符号为a，则不能匹配，表示无A⇒a...，或a不是A的后继符号。

### （2）符号栈：有四种情况

- 开始状态

符号栈

```text
#E

E#
xxxxxx#
```

- 工作状态

符号栈

```text
#....X
a.....#

X....#
```

查分析表得：

X ∈ Vₙ, M[X,a] = X::=αᵢ
X ⇒ a...

X ∈ Vₜ, X = a

|   | a |
|---|---|
| X | X::=αᵢ |

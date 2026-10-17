
## 4.4 Scope Rules

- scope of a name (variable, function, etc.); SEE CHAP2.4, 4.8
  the part of the program within which the name can be used.

- scope of an automatic variable:
  the function in which the name is declared

- scope of an external variable or a function:
  from the point at which it is declared to the end of the file
  if an external variable is to be referred to before it is defined
  or a name is defined in a different source file:
  an extern declaration is mandatory

```c
In file1:
extern int sp;
extern double val[];
void push(double f) {...}
void pop(void) {...}
```

```c
In file2:
int sp=0;
double val[MAXVAL];
```

## Discussion

- § 4.8 局部变量和全局变量
- 4.8.1 局部变量
- ☆ 在一个函数内部定义的变量是内部变量，它只在本函数范围内有效。

```c
float f1(int a)                 /* 函数f1 */
{
        int b, c;               a、b、c有效
        ……
}
```

```c
char f2(int x, int y)           /* 函数f2 */
{
        int a, b;               x、y、a、b有效
        ……
}
```

```c
main()                          /* 主函数 */
{
        int m, n;               m、n有效
        ……
}
```

### 【说明】

1、主函数main中定义的变量（m、n）也只在主函数中有效；主函数也不能使用其他函数中定义的变量。
2、不同函数中可以使用相同名字的变量，它们代表不同的对象，互不干扰。例如：在f1函数中定义了变量a，在f2函数中也定义了变量b，它们占据不同的内存单元。
3、形式参数也是局部变量。
4、可以在复合语句中定义变量，这些变量只在本复合语句中有效。

```c
main()
{
        int a, b;
        ……
        {
                int c;
                a、b在此范围内有效
                c = a + b;      c在此范围内有效
                ……
        }
}
```

![](img/1879308d3bf2ec0664445e4bc0146293_85_0.png)

## 4.5 Header Files

- place the definitions and declarations shared among the files in a *header file*.
- *example:*

### calc.h:

```c
#define NUMBER '0'
void push(double);
int getop(char []);
int getch(void);
void ungetch(int);
```

### main.c:

```c
#include <stdio.h>
#include <math.h>
#include "calc.h"
#define MAXOP 100
main() {
  ...
}
```

### getop.c:

```c
#include <stdio.h>
#include <ctype.h>
#include "calc.h"
getop() {
  ...
}
```

### stack.c:

```c
...
```

### getch.c

```c
...
```

## 4.6 Static Variables

- static:

### (1) applied to an external variables or function:

limits the scope of that object to the rest of the source file, the name is invisible outside the file.

```c
static char buf[BUFSIZE]; /* buffer for ungetch */
int getch(void) {...}
void ungetch(int c) {...}
```

### (2) applied to an internal variable:

the scope is the function (as an automatic variable), but it remains in existence as the program (not the function) is activated.

```c
void Example()
{
 static int i=1;
 printf("%d times\n", i++);
}

main()
{
 Example();
 Example();
 Example();
}
```

```text
1 times
2 times
3 times
```

static variables are initialized only the first time the function is entered.

## 4.7 Register Variables

- **register**: advises the compiler to place the variable in registers, in order to result in smaller and faster programs.
- **format**

```c
register int x;
register char c;
```

**example:**

```c
f(register unsigned m, register long n)
{
    register int i;
    ...
}
```

**notice:**

- ➢ *register declaration can only be applied to automatic variables and to the formal parameters of a function*
- ➢ *only a few variables can be kept in registers; excess declarations will be ignored.*
- ➢ *cannot take the address of a register variable*
- ➢ *there are restrictions on types of register variables.*

![](img/1879308d3bf2ec0664445e4bc0146293_89_0.png)

## 4.8 Block Structure

- **block: `{.....}`**
- variable can be declared in a block (follow the left brace); the scope of the variable is the block and remains in existence until matching the right brace.

```c
if(n>0) {
    int i;        /* declare a new i */
    for (i=0;i<n; i++)
    ...
}
```

the scope of “i”

The variable in an inner scope will hide variables in the outer scope of the same name.

```c
int x,y;
f(double x)
{  double y;
   ...
   x=y+1;
   ...
}
g()
...
```

inner first

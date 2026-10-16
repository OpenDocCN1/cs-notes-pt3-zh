
Hardware Event

System Queue

App3 Message Queue

App2 Message Queue

App1 Message Queue

Post Message

Application 1

Message Loop

Window Procedure

Default Window Procedure

Send Message

## 应用程序获得的消息

- 进队消息
  - 进队消息是由Windows放入程序的消息队列中的
- 不进队消息
  - 不进队消息直接发送给窗口过程

## CH1.2 SDK方式编写Windows应用程序

- □ 目标：能够用SDK (Windows API+C/C++)编写一个简单的Windows应用程序，通过编写程序掌握Windows程序的运行原理及编写方式。为MFC的学习打下基础。
- □ 掌握以下基本知识：
- ■ Windows应用程序基本结构

## 程序执行的起点(入口函数)?

main()

WinMain()

## WinMain函数

Windows程序的入口函数

```c
int WINAPI WinMain(
HINSTANCE hInstance,  // handle to current instance
HINSTANCE hPrevInstance,  // handle to previous instance
LPSTR lpCmdLine,  // command line
int nCmdShow  // show state
);
```

## 匈牙利表示法

- 一种命名约定

匈牙利命名法是微软推广的一种关于变量、函数、对象、前缀、宏定义等各种类型的符号的命名规范。匈牙利命名法的主要思想是：在变量和函数名中加入前缀以增进人们对程序的理解。

- 为纪念Microsoft程序员Charles Simonyi所使用的命名约定

## 命名约定

- 常用的命名约定有三种：
  - Unix环境常用的命名法
    - my_age、num_of_student
  - 驼峰式命名法
    - myAge、numOfStudent
  - 匈牙利标记法
    - iMyCar、bIsRight

## WinMain函数

## Windows程序的入口函数

```c
int WINAPI WinMain(
    HINSTANCE hInstance,
    // handle to current instance
    HINSTANCE hPrevInstance,
    // handle to previous instance
    LPSTR lpCmdLine,    // command line
    int nCmdShow        // show state
);
```

## 函数调用约定

函数调用是通过堆栈来实现的。在调用时，将参数值和调用后的返回地址压入所分配的堆栈空间中。函数计算结束以后，或者调用者、或者函数本身修改堆栈，使堆栈恢复原装。在参数传递中，有两个很重要的问题必须得到明确说明：

- 当参数个数多于一个时，按照什么顺序把参数压入堆栈
- 函数调用后，由谁来把堆栈恢复原装（堆栈清除）

栈底

较早的帧

参数n

调用者的帧

参数1

返回地址

帧指针 %ebp

被保存的%ebp

被保存寄存器、本地变量和临时变量

当前帧

栈指针 %esp

参数构造区域

栈顶

地址增大

## 函数的调用

函数调用过程的三个步骤

- 调用参数和返回地址（当前EIP）压栈，当前EBP压栈
- 跳转到函数入口，开始执行被调函数
- 恢复调用者原有栈，并跳到堆栈中保存的返回地址

## Windows系统的栈

低地址方向
esp→ 其他数据，例如被调函数的局部变量
esp→ EBP
esp→ EIP
esp→ 被调函数参数
esp→ 其他数据，例如上层函数的局部变量
SHE指针
高地址方向

## 函数调用过程示例

```
3 int func(int a, int b){
4   int retVal = a + b;
5   printf("b: 0x%08x\n", &b);
6   printf("a: 0x%08x\n", &a);
7   printf("ret addr here: 0x%08x\n", &a-1);
8   printf("stored ebp here: 0x%08x\n", &a-2);
9   printf("retVal: 0x%08x\n\n", &retVal);
10  return retVal;
11 }
12 int main(int argc, char* argv[])
13 {
14   int result = func(1, 2);
15   return 0;
16 }
```

![](img/6d59ef6ebdae7180bd2f8d0def48533b_72_0.png)

## 函数调用约定

在高级语言中，通过函数调用约定来说明这两个问题。常见的调用约定有：

- stdcall
- cdecl
- fastcall
- thiscall
- naked call

## 函数调用约定

| 关键字 | 清理堆栈 | 参数入栈顺序 |
|---|---|---|
| __cdecl | 调用函数 | 右 → 左 |
| __stdcall | 被调用函数 | 右 → 左 |
| __fastcall | 被调用函数 | 右 → 左 |

## 窗口的创建

创建一个完整的窗口需要经过下面四个操作步骤：

- 设计一个窗口类；
- 注册窗口类；
- 创建窗口；
- 显示及更新窗口。

## 窗口类的类型

在我们的程序中经常要用到一类变量，这个变量里的每一位(bit)都对应某一种特性。当该变量的某位为1时，表示有该位对应的那种特性，当该位为0时，即没有该位所对应的特性。当变量中的某几位同时为1时，就表示同时具有几种特性的组合。一个变量中的哪一位代表哪种意义，不容易记忆，所以我们经常根据特征的英文拼写的大写去定义一些宏，该宏所对应的数值中仅有与该特征相对应的那一位（bit）为1，其余的bit都为0。

## 窗口类的类型

如果我们希望某一变量的数值既有 CS_VREDRAW特性，又有CS_HREDRAW特性，我们只需使用二进制OR（|）操作符将他们进行或运算相组合，如style=CS_VREDRAW | CS_HREDRAW | CS_NOCLOSE。如果我们希望在某一变量原有的几个特征上去掉其中一个特征，用取反（~）之后再进行与（&）运算，就能够实现，如在刚才的style的基础上去掉 CS_NOCLOSE特征，可以用style & ~CS_NOCLOSE实现。

## 创建窗口 — 第一步

## 窗口类的定义— WNDCLASS

```
typedef struct tagWNDCLASS{
    UINT style;                 //窗口类风格
    WNDPROC lpfnWndProc;        //窗口过程函数
    int cbClsExtra;   //在类结构中预留的空间
    int cbWndExtra;           //在Windows内部预留空间
    HINSTANCE hInstance;      //程序实例句柄
    HICON hIcon;              //窗口的图标
    HCURSOR hCursor;          //光标句柄
    HBRUSH hbrBackground;     //背景色
    LPCTSTR lpszMenuName;     //窗口类菜单
    LPCTSTR lpszClassName;    //窗口类名
} WNDCLASS, *PWNDCLASS;
```

## 窗口过程函数

- □ 窗口过程函数用来对消息进行处理

第二个成员变量lpfnWndProc指定了这一类型窗口的过程函数，也称回调函数的。

## 回调函数

当应用程序收到给某一窗口的消息时（还记得前面讲过的消息通常与窗口相关的吗？），就应该调用某一函数来处理这条消息。这一调用过程不用应用程序自己来实施，而由操作系统来完成，但是，回调函数本身的代码必须由应用程序自己完成。

## 窗口过程函数

对于一条消息，操作系统到底调用应用程序中的哪个函数（回调函数）来处理呢？

操作系统调用的就是接受消息的窗口所属的类型中的`lpfnWndProc`成员指定的函数。

每一种不同类型的窗口都有自己专用的回调函数，该函数就是通过`lpfnWndProc`成员指定的。

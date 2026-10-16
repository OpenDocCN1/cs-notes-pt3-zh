

## 无符号数分析图

digits → **digit** num5  
num5 → **digit** num5 | ε

digit (digit)* (. digit (digit)*|ε) (E (+|-|ε) digit (digit)* |ε)

num4 → + digits | - digits | **digit** num5

num3 → **digit** num3 | E num4 | ε

num2 → **digit** num3

num1 → **digit** num1 | . num2 | E num4 | ε

num → **digit** num1

## 无符号数的正规文法

num → digit num1
num1 → digit num1 | . num2 | E num4 | ε
num2 → digit num3
num3 → digit num3 | E num4 | ε
num4 → + digits | - digits | digit num5
digits → digit num5
num5 → digit num5 | ε

## 无符号数 4.6E-8 的分析树

![](img/12b57169bd1d5004c5e7193ff0d478d5_99_0.png)

## 运算符

+ 关系运算符的正规表达式为：
+ < |<= | = | <> | >= | >

+ 正规定义式：
+ relop →< |<= | = | <> | >= | >

+ 关系运算符的正规文法：
+ relop → < | <equal | = |<greater | > | >equal
+ greater → >
+ equal → =

## 三、状态转换图与记号的识别

+ 状态转换图

+ 利用状态转换图识别记号

+ 为线性文法构造相应的状态转换图

+ 状态集合的构成

+ 状态之间边的形成

## 状态转换图

+ - 状态转换图是一张有限的方向图
  - 图中结点代表状态，用圆圈表示。
  - 状态之间用有向边连接。
  - 边上的标记代表在射出结状态下，可能出现的输入符号或字符类。

![](img/12b57169bd1d5004c5e7193ff0d478d5_102_0.png)

## 标识符的状态转换图

+ - 标识符的文法产生式：
  \( id \rightarrow \text{letter rid} \)
  \( rid \rightarrow \varepsilon \mid \text{letter rid} \mid \text{digit rid} \)

+ - 标识符的状态转换图

![](img/12b57169bd1d5004c5e7193ff0d478d5_103_0.png)

## 利用状态转换图识别记号

![](img/12b57169bd1d5004c5e7193ff0d478d5_104_0.png)

语句 D099K=1.10 中标识符 D099K 的识别过程

## 为线性文法构造相应的状态转换图

### 状态集合的构成

+ - 对文法G的每一个非终结符号设置一个对应的状态
  - 文法的开始符号对应的状态称为初态
  - 增加一个新的状态，称为终态。

### 状态之间边的形成

+ - 对产生式A→aB，从A状态到B状态画一条标记为a的边
  - 对产生式A→a，从A状态到终态画一条标记为a的边
  - 对产生式A→ε，从A状态到终态画一条标记为ε的边

## 无符号数的右线性文法的状态转换图

num → digit num1
num1 → digit num1 | . num2 | E num4 | ε
num2 → digit num3
num3 → digit num3 | E num4 | ε
num4 → + digits | - digits | digit num5
digits → digit num5
num5 → digit num5 | ε

![](img/12b57169bd1d5004c5e7193ff0d478d5_106_0.png)

### 3.4 词法分析程序的设计与实现

### 一、文法及状态转换图

+ 1. 语言说明

+ 2. 记号的正规文法

+ 3. 状态转换图

### 二、词法分析程序的构造

### 三、词法分析程序的实现

+ 1. 输出形式

+ 2. 设计全局变量和过程

+ 3. 编制词法分析程序

## 一、文法及状态转换图

## 语言说明

标识符：以字母开头的、后跟字母或数字组成的符号串。
保留字：标识符的子集。
无符号数：同PASCAL语言中的无符号数。
关系运算符：<、<=、=、<>、>=、>。
标点符号：+、-、*、/、（、）、:=、'、; 等。
赋值号： :=
注释标记：以 ‘/*’开始，以 ‘*/’结束。
单词符号间的分隔符：空格

## 记号的正规文法

+ - 标识符的文法
  \( id \rightarrow letter \ rid \)
  \( rid \rightarrow \varepsilon \mid letter \ rid \mid digit \ rid \)

+ - 无符号整数的文法
  \( digits \rightarrow digit \ remainder \)
  \( remainder \rightarrow \varepsilon \mid digit \ remainder \)

## 记号的正规文法（续）

### 无符号数的文法

num → digit num1
num1 → digit num1 | . num2 | E num4 | ε
num2 → digit num3
num3 → digit num3 | E num4 | ε
num4 → + digits | - digits |digit num5
digits → digit num5
num5 → digit num5 | ε

### 关系运算符的文法

relop →< |<equal | = |<greater |>|>equal
greater →>
equal → =

## 记号的正规文法（续）

### 赋值号的文法

assign_op → :equal
equal → =

### 标点符号的文法

single → + | - | * | / | ( | ) | : | ' | ;

### 注释头符号的文法

note → / star
star → *

## 状态转换图

![](img/12b57169bd1d5004c5e7193ff0d478d5_112_0.png)

### 二、词法分析程序的构造

根据上述状态转换图，再加上相应的语义动作，就可以构造出的词法分析程序的算法框图。

说明：R 为一过程，其功能是向前指针回退一个字符；Token 为字符数组，用于存放单词符号

## 三、词法分析程序的实现

+ 输出形式

+ 设计全局变量和过程

+ 编制词法分析程序

## 输出形式

+ - 利用翻译表，将识别出的单词的记号以二元式的形式加以输出
  - 二元式的形式：
    <记号，属性>

| 正规表达式 | 记号 | 属性 |
| --- | --- | --- |
| if | if | - |
| then | then | - |
| else | else | - |
| id | id | 符号表入口指针 |
| num | num | 常数表入口指针 / val |
| < | relop | LT |
| <= | relop | LE |
| = | relop | EQ |
| <> | relop | NE |
| > | relop | GT |
| >= | relop | GE |
| := | assign-op | - |
| + | + | - |
| - | - | - |
| * | * | - |
| / | / | - |
| ( | ( | - |
| ) | ) | - |
| , | , | - |
| ; | ; | - |
| : | : | - |

## 设计全局变量和过程

+ - 转换图中的每一状态，分别用一段程序实现。
  - 如果某一状态有若干条射出边，则程序：
    - 读一个字符
    - 根据读到的字符，选择标记与之匹配的边到达下一个状态，即程序控制转去执行下一个状态对应的语句序列。


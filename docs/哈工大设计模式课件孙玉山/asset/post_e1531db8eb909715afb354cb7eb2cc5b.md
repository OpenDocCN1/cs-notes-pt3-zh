
## 1. Evolution of Program Design

- All the program code are written in a single Continuous main program.
- Program written in unstructured language usually contains a series of statements.
- One line contains one statement, with a number label to denote the line number to allow the program execution can jump (use GOTO) from a line to another line
- Unstructured Languages: early BASIC, COBOL

## 1. Evolution of Program Design

The following is a piece of simple COBOL code, to show the features of unstructured programming

```
000100 IDENTIFICATION DIVISION.
000200 PROGRAM-ID. HAPPYNEWYEAR.
000300
100000 PROCEDURE DIVISION.
100100
100200 MAIN-LOGIC SECTION.
100300 BEGIN.
100400     DISPLAY " " LINE 1 POSITION 1 ERASE EOS.
100500     DISPLAY "Happy New Year!" LINE 15 POSITION 10
100600     STOP RUN.
100700 MAIN-LOGIC-EXIT.
100800 EXIT.
```

## 1. Evolution of Program Design

- Unstructured programming introduces: iteration, branch and GOTO
- Unstructured programming model does not have the procedure concept, but the primitive subroutines are allowed
- Here, the subroutine possibly has several entrance points and the exit points.
- The program control may go into or exit from this subroutine directly in any point
- This is not allowed in structured programming.

## 1. Evolution of Program Design

### 非结构化编程的样式

```
000100 statement 1
000200 statement 2
100200 statement 3, GO TO 100500
100300 statement 4
100500 statement 523, call Subroutine 1
100600
100700 statement 800
100800
100000 PROCEDURE DIVISION.
100100 Subroutine 1 {...}
Subroutine 2 {...}
Subroutine 3 {...}
Subroutine 4 {...}
Subroutine 5 {...}
```

程序执行顺序：按照顺序执行程序序，遇go to x语句，跳转到x行

可以在一个语句中 调用某个子程序

子程序甚至没有参数传递，可能有几个入口和出口。仅仅是为了反复调用一段程序提供方便。

## 1. Evolution of Program Design

- **Disadvantages of Unstructured programming:**
  a) It is difficult to follow program logic.
  b) It is hard to incorporate other code;
  c) It is not easy to modify code (都是goto惹的祸)
  d) It is difficult to test particular portions of the code

## 1. Evolution of Program Design

- **Structured programming** is a programming paradigm aimed on improving the clarity, quality, and development time of a computer program by making extensive use of
  - 子程序： **subroutines**,
  - 块状结构： **block structures** and
  - 循环结构： for and **while loops**.
- 结构化编程抛弃了GOTO语句。
- **Language that support structured programming:** started from ALGOL68, C

## 1. Evolution of Program Design

- **结构化程序定理：** 只要一种编程语言可以依三个方式组合其子程序及调整控制流程，则每个可计算函数都可以用此种编程语言来表示（实现任何算法）。三个调整控制流程的方式为：
  ◆ **序列结构：** 按照顺序执行一个子程序，然后再执行另一个子程序
  ◆ **选择结构：** 根据布尔表达式的值，执行两个子程序中的一个子程序（if, else if, else）；
  ◆ **迭代结构(for, while)：** 执行子程序，直到一个布尔表达式为true

## 1. Evolution of Program Design

序列结构

选择结构

循环结构

![](img/95717dc23f76db2057b9aa0c49790307_47_0.png)

## 1. Evolution of Program Design

- 该定理强调使用子程序、块状结构和for和while循环；而不是使用简单测试后再使用跳跃语句，例如goto语句；
- 该定理保证了只要一种编程语言支持序列结构、选择结构、循环结构(而不必使用goto语句语句)，则可以实现任何可计算函数；
- 该定理是结构化编程的理论基础。

## Call and Return Architecture

## 2. Call and Return Architecture

- **Call and return architecture** has been of a great influence for the past 30 years
- The **Main Program and Subroutine architecture** and **OO System** in this lecture are sub types of the call and return architecture

## 2. Call and Return Architecture

- A system designed in call and return architecture uses divide and conquer strategy.
- Its main idea is to divide the whole system into some smaller blocks to reduce the complexity and enhance the modifiability
- The execution order of the Call and return system is usually controlled by a single thread

## Main Program and Subroutine

是一种Call and return 架构
代表结构化编程

## 2. Main Program and Subroutine

### Main Program/Subroutine Pattern

The program is composed of a main program and some subroutines

![](img/95717dc23f76db2057b9aa0c49790307_54_0.png)

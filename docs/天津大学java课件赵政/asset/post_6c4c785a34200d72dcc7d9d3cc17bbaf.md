

## 3.10.1 类型提升的约定

- byte 型和 short 型提升到 int 型。
- 如果一个操作数是 long 型，整个表达式将被提升到 long 型。
- 如果一个操作数是 float 型，整个表达式将被提升到 float 型。
- 如果有一个操作数是 double 型，计算结果就是 double 型。

### 例 P42

```java
class Promote {
    public static void main(String args[]) {
        byte b = 42;
        char c = 'a';
        short s = 1024;
        int i = 50000;
        float f = 5.67f;
        double d = .1234;
        double result = (f * b) + (i / c) - (d * s);
        // b -> float : float,  c -> int : int,  s -> double : double
        // float + int - double  → double
        System.out.println((f * b) + " + " + (i / c) + " - " + (d * s));
        System.out.println("result = " + result);
    }
}
```

## 3.11 数组

- 数组（array）是相同类型变量的集合。
- 可以使用共同的名字引用它。
- 数组可被定义为任何类型。
- 可以是一维或多维。
- 数组是通过下标来访问它。

### 3.11.1 一维数组

- 一维数组实质上是相同类型变量列表。
- 一维数组的声明格式是：

```java
type var-name[ ];
int month_days[ ];
```

- 用运算符 `new` 分配地址并把它赋给数组的形式如下：

```java
var-name = new type[size];
month_days = new int[12];
```

- 你可以在方括号内指定它的下标来访问数组中特定的元素。所有的数组下标从零开始

```java
month_days[1] = 28; // 值28赋给数组的第2元素
```

### 例 P44 定义的数组存储了每月的天数

```java
// Demonstrate a one-dimensional array.
class Array {
  public static void main(String args[]) {
    int month_days[];
    month_days = new int[12];
    month_days[0] = 31;
    month_days[1] = 28;
    month_days[2] = 31;
    month_days[3] = 30;
    month_days[4] = 31;
    month_days[5] = 30;
    month_days[6] = 31;
    month_days[7] = 31;
    month_days[8] = 30;
    month_days[9] = 31;
    month_days[10] = 30;
    month_days[11] = 31;
    System.out.println("April has " + month_days[3] + " days.");
  }
}
```

Ans:

April has 30 days.

![](img/489adce8323ca3a7b0e9fe701e6e665c_100_0.png)

### 例 P44

```java
// An improved version of the previous program.
class AutoArray {
    public static void main(String args[]) {
        int month_days[] = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30,
            31 };
        System.out.println("April has " + month_days[3] + " days.");
    }
}
```

Ans: 同上题

April has 30 days.

### Java 严格地检查数组越界

例 P45 运用一维数组来计算一组数字的平均数

```java
class Average {
    public static void main(String args[]) {
        double nums[] = {10.1, 11.2, 12.3, 13.4, 14.5};
        double result = 0;
        int i;
        for(i=0; i<5; i++)
            result = result + nums[i];
        System.out.println("Average is " + result / 5);
    }
}
```

Ans:

Average is 12.3

### 3.11.2 多维数组

- 在Java中，多维数组实际上是数组的数组。
- 下面语句定义了一个名为 twoD 的二维数组变量。

```java
int twoD[][] = new int[4][5];
```

- 该语句分配了一个4行5列的数组并把它分配给数组 twoD。
- 二维数组（4行5列）的概念性表示

![](img/489adce8323ca3a7b0e9fe701e6e665c_104_0.png)

例 P46上 从左到右，从上到下为数组的每个元素赋值，显示数组的值

```java
// Demonstrate a two-dimensional array.
class TwoDArray {
    public static void main(String args[]) {
        int twoD[][] = new int[4][5];
        int i, j, k = 0;
        for(i=0; i<4; i++)
            for(j=0; j<5; j++) {
                twoD[i][j] = k;
                k++;
            }
        for(i=0; i<4; i++) {
            for(j=0; j<5; j++)
                System.out.print(twoD[i][j] + " ");
            System.out.println();
        }
    }
}
```

Ans:

0 1 2 3 4
5 6 7 8 9
10 11 12 13 14
15 16 17 18 19

- 当你给多维数组分配内存时，你只需指定第一个（最左边）维数的内存即可。
- 你可以单独地给余下的维数分配内存。
- 例如

```java
int twoD[][] = new int[4][];
twoD[0] = new int[5];
twoD[1] = new int[5];
twoD[2] = new int[5];
twoD[3] = new int[5];
```

- 程序定义了一个二维数组，它的第二维的大小可以是不相等的。

![](img/489adce8323ca3a7b0e9fe701e6e665c_107_0.png)

例 P46下 三维数组第二维的大小是不相等

```java
// Manually allocate differing size second dimensions.
class TwoDAgain {
  public static void main(String args[]) {
    int twoD[][] = new int[4][];
    twoD[0] = new int[1];
    twoD[1] = new int[2];
    twoD[2] = new int[3];
    twoD[3] = new int[4];
    int i, j, k = 0;
    for(i=0; i<4; i++)
      for(j=0; j<i+1; j++) {
        twoD[i][j] = k;
        k++;
      }
    for(i=0; i<4; i++) {
      for(j=0; j<i+1; j++)
        System.out.print(twoD[i][j] + " ");
      System.out.println();
    }
  }
}
```


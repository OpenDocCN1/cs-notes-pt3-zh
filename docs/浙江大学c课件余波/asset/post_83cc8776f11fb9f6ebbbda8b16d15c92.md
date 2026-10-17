
# 第八章 指针和引用

（3）如果要给一个指针赋一个常量的地址，则这个指针必须定义为指向常量的指针。

如：

```cpp
const int ci = 30;
const int *ip1 = &ci; // (√)
int *ip2 = &ci;       // (×)
```

## 二、指针常量

1、定义：在指针变量名前加 const。

如：

```cpp
int i;
int * const ip = &i;
```

## 三、指向常量的指针常量

1、定义：在指针定义前和变量名前各加一个 const。

如：

```cpp
int i;
const int * const ip = &i;
```

2、含义：既不能改变指针变量本身的值，也不能改变指针所指的数据。

如：

```cpp
int i, j;
const int * const ip = &i;
ip = &j; // (×)
*ip = 32; // (×)
```

## § 8.5 指针与数组

### 一、一维数组的数组名是指向该数组首元素的指针。

如：

```cpp
int array[5] = {10, 20, 30, 40, 50};
```

则：

```cpp
array = &array[0];
```

### 二、指向数组的指针可以当作数组名使用。

如：

```cpp
int array[100];
int *pArray = array;
```

则 `pArray` 为指向一维数组的指针，此时访问数组中第 i+1 个元素，下面两种方式是等价的：

`array[i]` ←———→ `pArray[i]`

例：

```cpp
#include <iostream.h>
void main()
{
    int array[5];
    int *pArray = array;
    for (int i = 0; i < 5; i++)
    {
        array[i] = i;
        cout << pArray[i] << " " << array[i] << endl;
    }
}
```

此程序的运行结果为：

0 0
1 1
2 2
3 3
4 4

### 三、数组名是指针常量，而不是指针变量。

如：

```cpp
int array[100];
```

则：

```cpp
array = &array[1]; // (×)
```

### 四、指针的加减

#### 1、指针加减的含义：

- ☆ 指针 + 1：指针向后移动一个数组元素。
- ☆ 指针 - 1：指针向前移动一个数组元素。

如：

```cpp
int array[5] = {10, 20, 30, 40, 50};
int *pa = array;
```

2、指针的加减是以指针所指数据的类型大小为单位进行的。
（例见 181 页—182 页）

注：如果指针指向的是一个结构数组，则指针的运算就以一个结构元素所占内存空间大小为单位。
（例见 182 页）

## 五、用指针对数组进行操作

### 1、通过指针的加减来访问数组元素。（例见 183 页、184 页）

### 2、访问数组的第 i+1 个元素的四种方式：

若有：

```cpp
int array[5] = {10, 20, 30, 40, 50};
int *pa = array;
```

则有：

- `pa[i]`
- `array[i]`
- `*(pa + i)`
- `*(array + i)`

### 3、取数组中第 i+1 个元素地址的四种方式：

若有：

```cpp
int array[5] = {10, 20, 30, 40, 50};
int *pa = array;
```

则有：

- `&pa[i]`
- `&array[i]`
- `pa + i`
- `array + i`

### 4、在对指针进行加减运算时，必须保证经过运算得到的新地址是程序能够支配的地址。

若有：

```cpp
int array[10];
int *pa = array;
```

则：

```cpp
pa + 20; // (×)
```

## 六、指针与字符串

- 1、字符串：以 `'\0'` 为结束符的字符序列。
- 2、可以将字符指针看成是一个字符串。如：`char *str = "a string";`
- 3、输出字符指针将输出整个字符串。如：`char *str = "a string"; cout << str;` → 输出：`a string`
- 4、输出对一个字符指针的间接引用时，将会输出字符串的第一个字符。如：`cout << *str;` → 输出：`a`

## § 8.6 动态内存申请

### 一、new 与 delete

#### 1、内存空间申请

##### （1）new 操作符：表示从堆内存中申请一块空间。

##### （2）返回值：

申请成功：返回所申请到的空间的首地址。申请失败：返回空指针（NULL）。

##### （3）new 的三种格式：

- ★ new 数据类型
- ★ new 数据类型（初始化值）
- ★ new 数据类型[常量表达式]

例：

```cpp
int *ip1 = new int;
int *ip2 = new int(3);
int *str = new int[10];
```

#### 2、内存空间释放

##### （1）delete 操作符：表示将从堆内存中申请的一块空间返还给堆。

##### （2）delete 的两种格式：

- ☆ delete 指针名
- ☆ delete [ ] 指针名

例：

```cpp
int *pInt = new int;
float *pFloat = new float(34.5);
int *arr = new int[100];
delete pInt;
delete pFloat;
delete[] arr;
```

☆在用 delete 来释放一个指针所指的空间时，必须保证这个指针所指的空间是用 new 申请的，并且只能释放这个空间一次。

例：

```cpp
int i;      int *ip = &i;       delete ip; // (×)
float *fp = new float(3.4);
delete fp; // (√)
delete fp; // (×)
```

- ☆如果在程序中用 new 申请了空间，就应该在结束程序前释放所有申请的空间。
- ☆当一个指针没有指向合法的空间，或者指针所指的内存已经释放以后，最好将指针的值设为 NULL。

## 二、指针与动态数组

1、若申请的是一个简单的数据空间，则可以通过间接访问操作符 * 来访问

```cpp
int* ip = new int;
*ip = 34;
cout << *ip;
```

## 3、指针数组

数组中的每个元素都是指针

例：

```cpp
char *week[7] = {"Sunday ", "Monday ", "Tuesday ", "Wednesday ", "Thursday ", "Friday ", "Saturday "};
```

## 三、指针与动态结构

### 1、利用指针访问结构成员

- ⭐ （* 指针名）.成员名
- ⭐ 指针名→成员名

例：

```cpp
struct Student
{
    char name[20];
    float score;
};
Student st = {"wanglin ", 98};
Student *ps = &st;
```

则有：

- `ps -> name == (*ps).name == st.name == "wanglin "`
- `ps -> score == (*ps).score == st.score == 98;`

### 2、链表

（1）链表是由若干个结点链接而成的

![](img/d4a5a3c164ae1bdac1a9c9c8d02b4697_282_0.png)

### （2）结点用结构类型来描述

结点由数据成员和指针成员组成。数据成员描述每一个结点的信息；指针成员用来指向链表中的下一个结点。

![](img/d4a5a3c164ae1bdac1a9c9c8d02b4697_283_0.png)

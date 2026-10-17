
## 1. 结构与类

```cpp
// 改用含成员函数的类来处理
class Clock
{
public:
    void setTime();
    void showTime();
private:
    int hour;
    int minute;
    int sec;
};

int main()
{
    Clock t1;
    t1.setTime();
    t1.showTime();
    Time t2;
    t2.setTime();
    t2.showTime();
    return 0;
}
```

## 2. 类的声明与定义

- 类是用户定义的数据类型，用关键字 `class` 声明。类包含两种成员：数据成员和成员函数。
- 类的定义指包含成员实现的类声明。
- 类使程序员可以构造对象的属性和行为或操作。

类一般定义格式如下：

```cpp
class ClassName {

private:

data member & member function;

public:

data member & member function;

};

Member function definition;
```

![](img/bf99340ecbaf09a3098cf7d9c4b141d1_25_0.png)

![](img/bf99340ecbaf09a3098cf7d9c4b141d1_25_1.png)

![](img/bf99340ecbaf09a3098cf7d9c4b141d1_25_2.png)

## 定义成员函数

### 1. 类外定义成员函数

```cpp
void Clock::setTime()
{
    cin >> hour;
    cin >> minute;
    cin >> sec;
}

void Clock::showTime()
{
    cout << hour << " :"
         << minute << " :"
         << sec << endl;
}
```

### 2. 类内定义成员函数

```cpp
class Clock
{
public:
    void setTime()
    {
        cin >> hour >> minute >> sec;
    }
    void showTime()
    {
        cout << hour << ":"
             << minute << ":"
             << sec << endl;
    }
private:
    int hour, minute, sec;
};
```

- 成员函数为描述对象的方法。
- 在类的外部定义成员函数：

```cpp
返回类型 类名::成员函数名(参数列表)
{
    函数定义体
}
```

- 在类内直接定义成员函数，默认创建为内联函数。
- 如果成员函数在类体外定义，要用 `inline` 声明为内联函数。

## 成员函数 vs. 一般函数

- 都有函数体，返回值和函数类型。
- 成员函数属于一个类的成员，可出现在类体中；在类体外定义时要加类名和作用域解析符 `::`。
- 成员函数和数据成员封装成一体，可直接引用数据成员。
- 成员函数只能由本类对象或者成员访问，访问说明符限制 `private`、`public`。

## 2. 类的声明与定义

类是一种用户自定义的数据类型，它的一般定义格式如下：

```cpp
class 类名 {

private:
    私有数据成员和成员函数；

protected:
    保护数据成员和成员函数；

public:
    公有数据成员和成员函数；

};

各个成员函数的实现；
```

## 3. 访问控制

- 成员访问说明符决定调用成员的权限以及它的作用域。
- 公有 `public`：说明为公有的成员可以被程序中的任何代码访问。
- 私有 `private`：说明为私有的成员只能被类本身的成员函数及友元类成员函数或友元函数访问；默认情况下，类的成员是私有的。
- 保护 `protected`：除了类本身的成员函数和说明为友元函数或友元类的成员函数可以访问保护成员外，该类的派生类的成员也可以访问。

```cpp
class A
{
private:             // 首次出现时可以省略
    int m_a;
    void set(int a) { m_a = a; }
public:              // 公有成员
    int m_b;
    void show();
};

void A::show() { cout << m_a << m_b << endl; }
```

```cpp
A a;    // 定义A类的对象a
a.m_a;
a.m_b;
a.show();
a.set(5);
```

- `private` 声明的数据和函数不能在类以外访问。
- `public` 声明的数据和函数可以在类以外访问。
- 默认为 `private` 访问类型。

```cpp
class A
{
public:
    int m_b;
    void show();
private:
    int m_a;
    void set(int a)
    { m_a = a; }
};
```

![](img/bf99340ecbaf09a3098cf7d9c4b141d1_32_0.png)

## 课堂练习：完成 Clock 类的定义并对其进行测试

增加 `void setTime(int h, int m, int s);`，注意时间有效性的判断。

应注意区分什么场合用域运算符 `::`，什么场合用成员运算符 `.`，不要搞混。

- 在主函数中调用两个成员函数时，应指明对象名，表示调用的是哪一个对象的成员函数。`Time t1, t2;  t1.setTime(); t2.showTime();`
- 在类外定义函数时，应指明成员函数的作用域 `void Clock::setTime() { cin >> hour >> minute >> sec; }`。在成员函数引用本对象的数据成员时，只需直接写数据成员名，这时 C++ 系统会把它默认为本对象的数据成员。

## 总结

- 类的概念
- 类与结构体的区别
- 类的声明
- 类的定义
- 访问权限

## 课堂练习：声明日期类

声明并定义描述日期的类，对该类进行测试。

```cpp
class Date
{
private:
    int month, day, year;
    int isLeapYear();
public:
    void set(int m, int d, int y);
    void show();
    int getYear();
    int getMonth();
    int getDay();
    int whichDay();
};
```

## 作业与上机

### 1. 盒子类 BOX

- 数据成员包括：`length`, `width`, `height`
- 成员函数实现以下功能：
  1. 由键盘分别输入三个盒子的长宽高；
  2. 输出盒子的属性；
  3. 计算长方体盒子的表面积和；
  4. 计算长方体盒子的体积。
- 编写基于对象的程序，对该类进行测试。

### 2. 日期类 Date

- 私有数据成员 `year`, `month`, `day`；
- 公有成员函数实现以下功能：
  1. 设置时间，并对该时间的有效性进行检测；
  2. 输出时间，按 `mm/dd/yyyy` 方式打印；
  3. 判断该日期是一年的第几天；
  4. 判断该日期是星期几（选作）。
- 编写一个驱动程序进行测试。

### 3. 时间类 Time

- 私有数据成员 `int hour, minute, second`
- 公有成员函数：自定义

用一个 `tick` 成员函数将 Time 对象中存放的时间递增 1 秒。  
Time 对象应该总是保持一致状态。编写一个驱动程序，  
在循环中测试 `tick` 成员函数，按标准格式打印时间，从而  
演示 `tick` 成员函数的工作情况。要保证测试下列情况：  
a) 递增到下一分钟。  
b) 递增到下一小时。  
c) 递增到下一天（即 11:59:59 PM 到 12:00:00 AM）。

### 4. Student 类

每个学生包含姓名、年龄、学号、性别等属性，并且实现显示和设置这些属性的成员函数。

要求：第一次上机检查！

| Student |
| --- |
| `char name[10]` |
| `int no` |
| `char sex` |
| `void set();` |
| `void set(char*, int, char);` |
| `void get();` |
| `char* getName();` |

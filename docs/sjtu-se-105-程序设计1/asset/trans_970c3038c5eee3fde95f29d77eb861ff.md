

| 符号 | 表示 |
| --- | --- |
| 换行符 | \n |
| 水平制表键 | \t |
| 垂直制表键 | \v |
| 退格键 | \b |
| 回车键 | \r |
| 反斜杠键 | \\ |
| 单引号 | \' |
| 双引号 | \" |
| 1~3位八进制数 | \ddd |
| 1~2位十六进制数 | \xhh |
| 问号 | \? |

## 字符串

- 字符串字面常量由零个或多个用双引号括起来的字符组成
- 不可打印字符可以由相应的转义序列来表示
- 一个字符串文字可以扩展到多行，在一行的最后加上一个反斜杠表明字符串文字在下一行继续

- "" (空字符串)
- "a"
- "\nCC\toptions\tfile.[cC]\n"
- "a multi-line \
string literal signals its \
continuation with a backslash "
- cout << "\nCC\toptions\tfile.[cC]\n";

## bool型

- 单词true 和 false 是bool型的字面常量

- 内置类型
- 布尔类型
  - bool
- 字符类型
  - char
- 整数类型
  - int
  - and short and long
- 浮点数类型
  - double
  - and float
- 标准库类型
  - string

- 布尔字面常量
- true false
- 字符字面常量
- 'a', 'x', '4', '\n', '$'
- 整数字符常量
- 0, 1, 123, -6, 0x34, 0xa3
- 浮点数字符常量
- 1.2, 13.345, 0.3, -0.54, 1.2e3, 0.3F
- 字符字面常量
- "asdf", "Howdy, all y'all!"

- 在前面的程序中，我们读入了一个变量的值
  - 这里是 first_name
- 读入的变量具有类型
  - 这里是 string
- 变量类型确定了在变量上可以执行何种操作
  - 这里是 cin >> first_name;
  - 即读入字符直至遇到空白符(whitespace)
  - 空白符：空格( space)、制表符(tab)、换行(newline) ...

## 字符串输入

```cpp
// 读入 first和second:
int main()
{
    cout << "please enter your first and second names\\n";
    string first;
    string second;
    cin >> first >> second;                 // 读入两个字符串
    string name = first + ' ' + second;     // 连接字符串，用空格分开
    cout << "Hello, " << name << '\\n';
}

// 省略了 #include “std_lib_facilities.h” 以节省空间
// 在实际代码中不要忘记
```

```
// 读入名字和年龄
int main()
{
    cout << "please enter your first name and age\n";
    string first_name;        // 字符串变量
    int age;                  // 整数变量
    cin >> first_name >> age;    // 读入
    cout << "Hello, " << first_name << " age " << age << '\n';
}
```

- >> 是对类型敏感的
  - 根据读入的变量类型来读取输入值
  - 输入 22 Carlos 会如何？
  - 对变量赋初值可以防止这种错误

```
// 简单的算术运算

int main()
{
    cout << "please enter a floating-point number: ";
    double n;                         // 浮点数变量
    cin >> n;
    cout << "n == " << n
         << "\nn+1 == " << n+1          // '\n' 表示“换行"
         << "\nthree times n == " << 3*n
         << "\ntwice n == " << n+n
         << "\nn squared == " << n*n
         << "\nhalf of n == " << n/2
         << "\nsquare root of n ==" << sqrt(n)   // 库函数
         << endl;                        // 换行的另一个名字
}
```

## 数字与字符串

- **字符串**
  - `cin >>` 读入（直至遇到空白符）
  - `cout <<` 写出
  - `+` 连接
  - `+= s` 将字符串 s 追加到末尾
  - `++` 不支持该操作
  - `--` 不支持该操作
  - `...`

- **整数与浮点数**
  - `cin >>` 读入一个数字
  - `cout <<` 写出
  - `+` 加
  - `+= n` 加上 int n
  - `++` 自增 1
  - `--` 减法
  - `...`

变量的类型决定了哪些操作是合法的，以及这些操作对于该类型具有何种含义

> （这被成为“重载 overloading”或“操作符重载 operator overloading”）

```
string a = "alpha";

a = "beta";

string b = a;

b = a + "gamma";

a = a + "delta";
```

a: alpha

a: beta

a: beta
b: beta

a: beta
b: betagamma

a: betadelta
b: betagamma

```
int main()
{
    string previous = " ";    // 初值
    string current;
    while (cin>>current) {    // 读入单词流
        if (previous == current) // 检查新输入单词是否与最后一个输入单词相同
            cout << "repeated word: " << current << '\n';
        previous = current;
    }
}
```

- 探测是否连续输入了相同的词
  - While

## 简单计算

```
int main()
{
    const double cm_per_inch = 2.54;    // 1英寸=2.54厘米
    int length = 1;                    // 英寸长度
    while (length != 0)                // 英寸长度如果为 0，则终止
    {
        cout << "Please enter a length in inches: ";
        cin >> length;
        cout << length << "in. = "
             << cm_per_inch*length << "cm.\n";
    }
}
```

- while语句重复执行，直至条件为假

## 复合赋值操作符

++counter → counter = counter + 1

```
a += 7;  // means a = a+7
b -= 9;  // means b = b-9
c *= 2;  // means c = c*2
```

a oper= b → a = a oper b

+=, -=, *= , /=, %=

```
int a = 7;    // int 类型变量 a，初始化为整数值 7
```

7

```
a = 9;    // 赋值: 现在将 a 的值改为 9
```

9

```
a = a+a;    // 赋值: now double a's value
```

18

```
a += 2;    // 自增 a 的值 2
```

20

```
++a;    // 自增 a 的值 1
```

21




## 字符串输入函数

- `istream& istream::get(char* &pArray, streamsize n, char delim = '\n');`

作用：读取一段文本，并将输入的字符串以及一个空字符一起存储，**将指定的终止符留在流中。**  
如读取失败（遇 EOF）则流 istream 对象设置错误标志，不能继续进行输入操作。

```cpp
char str[20];
cin >> str;
cin.get(str, 20);
```

## 9.3 流操作

### 运行并分析输出结果

```cpp
char ch1[20], ch2[20], ch3[20], ch4[20];

cin >> ch1;                 cout << ch1 << endl;

cin.get(ch2, 10);           cout << ch2 << endl;

cin.get(ch3, 20);           cout << ch3 << endl;

cin.get(ch4, 20, ' ');      cout << ch4 << endl;
```

## 9.3 流操作

### 字符串输入函数

```cpp
istream& istream::getline(char* &pArray,
    streamsize n, char delim = '\n');
```

**作用：** 从输入流中读取 n-1 个字符，赋给指定的字符数组，如果在读取 n-1 个字符之前遇到指定的字符则读取结束。如果读取成功则函数返回非 0 值（真），否则（遇到文件结束符）则函数返回 0 值（假）。

从流中提取字符串后流中删除分隔符，继续读取的字符串从分隔符后面的字符开始。

## 9.3 流操作

### 运行 ch9_5.cpp 并分析输出结果

```cpp
char ch1[20], ch2[20], ch3[20], ch4[20];

cin >> ch1;                  cout << ch1 << endl;

cin.getline(ch2, 10);        cout << ch2 << endl;

cin.getline(ch3, 20);        cout << ch3 << endl;

cin.getline(ch4, 20, ';');   cout << ch4 << endl;
```

## 9.3 流操作

### 9.3.3 输入输出流的错误

为了保证程序能够安全进行输入输出操作，C++ 提供了检测 I/O 流状态的标志和成员函数。在流类中包含一个描述流状态的数据成员 state，这个状态字中特定位记录流处于正常状态或不同的错误状态。

| 标识常量 | 值 | 意义 |
|---|---|---|
| ios::goodbit | 0x00 | 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 |
| ios::eofbit | 0x01 | 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 1 |
| ios::failbit | 0x02 | 0 0 0 0 0 0 0 0 0 0 0 0 0 0 1 0 |
| ios::badbit | 0x04 | 0 0 0 0 0 0 0 0 0 0 0 0 1 0 0 0 |

## 9.3 流操作

### 9.3.3 输入输出流的错误

流类提供一些成员函数用于测试或设置流对象的状态，常用函数

| 函数 | 功能 |
|---|---|
| int eof() const; | 返回 eofbit 状态值。文件结束符时返回 1，否则返回 0 |
| int fail() const; | 返回 failbit 状态值 |
| int bad() const; | 返回 badbit 状态 |
| int good() const; | eofbit、failbit 和 badbit 都没有被设置，则返回 1 |
| int rdstate() const; | 返回状态字 |
| void clear(int n = 0); | 恢复或设置状态字 |

## 9.3.4 重载流插入和提取运算符

C++ 中定义的位左移运算符“<<”和位右移的运算符“>>”进行位运算，在流类中对它们进行了重载，使之作为流插入运算符和流提取运算符，用来对各种基本类型的数据进行输出和输入操作。

## 9.3.4 重载流插入和提取运算符

### 重载流插入运算符 <<

ostream 流类中为基本类型数据重载“<<”，有如下形式：

```cpp
ostream & ostream::operator << (int);
ostream & ostream::operator << (float);
ostream & ostream::operator << (char);
ostream& ostream::operator<< (const void *);
ostream& ostream::operator<< (const char *);
```

可以在用户自定义的类 A 中重载该运算符  
A 类中定义如下友元函数：

```cpp
friend ostream& operator << (ostream& out, const A&);
```

## 9.3.4 重载流插入和提取运算符

### 重载流提取运算符 >>

istream 类中重载了一组成员函数 operator >>（），对于各种基本类型 T 的数据，定义成员函数重载该运算符：

```cpp
istream& istream::operator>>(T& data);
istream& istream::operator>>(char *);
```

可以在用户自定义的类 A 中重载 >> 运算符  
A 类中定义如下友元函数：

```cpp
friend istream & operator >> (istream &, Type&);
```

## 9.4 文件流

### 数据的层次结构

Bit – Byte – Field – Record – File - DBMS

### 文件的概念

存储在外部介质中的数据集合称为文件。

C++ 把文件看成有序的字节流，提供低级和高级的 I/O 功能

- 一批数据通常是以文件的形式存放在外部介质上的。
- 操作系统是以文件为单位对数据进行管理。

## 9.4 文件流

### 知识要点

- 文件以及文件流的概念
  - 数据流方向，文本文件与二进制文件
  - 文件流类与文件流对象

- 文件的打开与关闭
  - 打开方式

- 文本文件的顺序读写操作
  - `<<, >>, put, get(), getline(), read(), write()`

- 二进制文件的随机读写操作

## 9.4 文件流

### 9.4.1 文件流类与对象

文件流是以外存文件为输入输出对象的数据流。  
输出文件流是从内存流向外存文件的字节序列，  
输入文件流是从外存文件流向内存的字节序列。  
每一个文件流都有一个内存缓冲区与之对应。  
I/O 类库中定义了以下三种文件流进行文件读写操作。

1. ifstream 类  
   从输入流 istream 类派生的，支持从磁盘文件的输入。

2. ofstream 类  
   从输出流 ostream 类派生的，支持向磁盘文件的输出。

3. fstream 类  
   从输入输出流 iostream 类派生的，支持对磁盘文件的输入输出。

## 9.4 文件流

### 9.4.1 文件流类与对象

ifstream、ofstream 和 fstream 类对象  
用于内存与文件之间的数据传输

## 9.4 文件流

### 9.4.1 文件流类与对象

C++ 把文件看成有序的字节流，提供低级和高级的 IO 功能

- 使用方式：程序文件 / 数据文件
- 存取方式：顺序读写文件 / 随机读写文件
- 编码方式：文本文件 / 二进制文件

➤ 文本模式  
— 任何数据被解释为一系列的字符，  
  内存中存储的二进制数据需要转换为字符的形式。  
➤ 二进制模式  
— 无需进行格式的转换，流中直接传送原始字节数据。

## 文件操作的基本步骤：

1. 打开文件
   ```cpp
   streamclass fileObj (fileName , openMode );
   fileObj.open( fileName , openMode );
   ```

2. 读 / 写文件
   ```cpp
   << , put(),         write()
   >> , get(),getline(), read()
   ```

3. 关闭文件
   ```cpp
   fileObj.close( );
   ```




## More examples of cout

std::cout << "data1" << "data2";

// puts two piece into the stream

How do you think will they display on the screen?

- a) data1  data2
- b) data1
  data2
- c) data1data2

## More examples of cout

Here is the code to get the different options

a) data1 data2

std::cout << "data1" << "data2";

## More examples of cout

Here is the code to get the different options

a) data1 data2
std::cout << "data1" << "data2";

b) data1
data2
std::cout << "data1\n" << "data2";

## More examples of cout

Here is the code to get the different options

a) data1 data2
std::cout << "data1" << "data2";

b) data1
data2
std::cout << "data1\n" << "data2";

c) data1data2
std::cout << "data1" << "data2";

## Different ways to do the same thing

```
std::cout << "data1" << "data2";
```

```
std::cout << "data1data2";
```

```
std::cout << "data1"
<< "data2";
```

```
std::cout << "data1";
std::cout << "data2";
```

> Note: all these statements do the same thing

## Different types of data

`"data"` string, text, or string literal

`'d'` character, or char

`42` number, integer, or int

.....more information later

## cout and different kinds of data (more examples)

```
std::cout << "5 + 4 = " << 5 + 4 ;
```

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_101_0.png)

## String Literals

- **String Literals** (sometimes called a **string**)
  - 0 or more character inside of “  “
  - when a string literal is sent to cout it will display all the characters that are inside the “  “ just as they are shown.

```
std::cout << “hello world”;
```

```
hello world
```

## String Literals

- That is true most of the time......
  - what do you think this would do?

std::cout << “He said “Hello there” ” ;

## String Literals

- That is true most of the time……
  - what do you think this would do?

```
std::cout << “He said “Hello there” ”;
```

COMPILE ERROR: Because the “ is used to mark the beginning and end of a string literal

## String Literals

- If we want do display a “ then we must put a signal in the string to tell it

```
std::cout << "He said \"Hello there\" ";
```

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_106_0.png)

## Number Data types in C++

C++ has two main number types

- **Integer:** （整数 zhēng shù）
  - whole numbers  -2,  -1,  0,  1,  2
- **Floating-point:** （浮点数 fú diǎn shù）
  - decimal numbers    -2.5,  0.0,  2.5,

## Numbers and Math Operators

```cpp
// integer division
std::cout << "5 / 4 = " << 5 / 4 << std::endl;
```

5 / 4 = 1

## Numbers and Math Operators

```cpp
// integer division
std::cout << "5 / 4 = " << 5 / 4 << std::endl;
```

```cpp
// floating point division
std::cout << "5 / 4.0 = " << 5 / 4.0 << std::endl;
```

```
5 / 4 = 1
5 / 4.0 = 1.25
```

## Integers and Modulus Operator

```cpp
// integer division
std::cout << "6 / 4 = " << 6 / 4 << std::endl;
```

```
6 / 4 = 1
```

## Integers and Modulus Operator

```cpp
// integer division
std::cout << "6 / 4 = " << 6 / 4 << std::endl;

// modulus operation (remainder)
std::cout << "6 % 4 = " << 6 % 4 << std::endl;
```

```
6 / 4 = 1

6 % 4 = 2
```

## Something to think about

- Let x be some whole positive number
  then what are the answers to the following

x % 1 → [ ? ]

x % 2 → [ ? ]

x % 3 → [ ? ]

## Something to think about

- Let x be some whole positive number then what are the answers to the following

- x % 1 → [ 0 ]

- x % 2 → [ 0, 1 ]

- x % 3 → [ 0, 1, 2 ]

## Something to think about

- Let x be some whole **positive** number then what are the answers to the following

  - x % 1 → [ 0 ]

  - x % 2 → [ 0, 1 ]

  - x % 3 → [ 0, 1, 2 ]

so if n is some **positive** number

- x % n → [ 0, ... n-1 ]


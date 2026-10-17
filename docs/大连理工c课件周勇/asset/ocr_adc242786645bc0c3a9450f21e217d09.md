# # 类声明和成员函数定义的分离

# ## 1. 自定义类库头文件.h

文件中有用户自行设计的类的定义，包括类的外部接口（公有成员函数的原型）。任何需要使用这些类的源程序，只要在文件中包含这些头文件即可。

```
```cpp
// date.h
class Date{
public:
void set(int m,int d,int y);
int isLeapYear();
void print();
private:
int month, day, year;
};
```
```
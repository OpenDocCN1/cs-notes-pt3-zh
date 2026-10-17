# # 第5章 继承

例5.1 访问公有继承的成员

```
```cpp
class Student {
    // 学生类(基类)
protected:
    char name[10];
    char sex;
    int number;
    char school[10];  // 学校
public:
    void input_data();  // 输入学生信息函数
    void print();  // 输出学生信息函数
};
```
```

大连理工大学软件学院
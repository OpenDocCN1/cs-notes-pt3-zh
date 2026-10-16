# 结构体类型变量的定义(2)

+   • 定义结构体类型的同时定义结构体变量

一般形式：

```
例  struct student
{  int num;
    char name[20];
    char sex;
    int age;
    float score;
    char addr[30];
}stu1,stu2;
```

```
struct 结构体名
{
    类型标识符  成员名;
    类型标识符  成员名;
    ............
}变量名表列;
```
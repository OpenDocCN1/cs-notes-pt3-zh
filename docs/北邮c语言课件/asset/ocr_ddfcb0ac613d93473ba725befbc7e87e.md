# 结构体变量的初始化（2）

+   - 形式二：

```
struct 结构体名
{
    类型标识符  成员名;
    类型标识符  成员名;
}
}结构体变量={初始数据};
```

```
例  struct student
    {
        int num;
        char name[20];
        char sex;
        int age;
        char addr[30];
    }stu1={112, “Wang Lin”, ‘M’, 19, “200 Beijing Road”};
```
# 结构体数组初始化与引用

+   - 结构体数组初始化

+   - 结构体数组引用

引用方式：结构体数组名[下标].成员名

```
struct student
{
    int num;
    char name[20];
}str[3];
```

```
struct student
{
    int num;
    char name[20];
    char sex;
    int age;
}str[3];
```

```
str[0] = {1, "Wang Lin", 'M', 20};
str[1] = {2, "Li Gang", 'M', 19};
strcpy(str[0].name, "Zhao Da");
```

```
stu[1].age++;
```

全部初始化时维数可省
# # 消息映射原理

# □ 消息映射表的实现方式

+   - MFC通过宏定义实现在类的静态消息映射表

+   - 在类的定义文件中加入(声明消息映射)

```
DECLARE_MESSAGE_MAP()
```

+   - 在类的实现文件中加入(表和表项的定义)

```
BEGIN_MESSAGE_MAP(theClass, baseClass)
    ......              // 当前类，当前类的父类
    //
END_MESSAGE_MAP()
```
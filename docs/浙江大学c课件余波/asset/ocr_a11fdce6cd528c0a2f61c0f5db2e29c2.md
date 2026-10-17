# # 第六章 简单程序设计

# ## 6、静态局部变量

（1）在一般局部变量的定义前加上static例：

```
int addCount()
{
    static int count;
    count++;
    return count;
}
```
# # 第五章 函数

# ## 六、const参数、const返回值与const函数

# ### （一）const参数

1、出现在函数参数中的const表示在函数体中不能对这个参数做修改。

2、const通常用来限制函数的指针参数、引用参数和数组参数。

如：int strcmp(const char*str1, const char*str2);
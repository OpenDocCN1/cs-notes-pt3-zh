# 运算 string.h

- 两个字符串比较大小或比较是否相等，按字典顺序进行。

+   调用方式 i=strcmp(st1,st2);

+   返回值

+   1 说明st1的值大于st2

+   0 说明st1的值等于st2

+   -1说明st1的值小于st2

+   例子

+   -strcmp(st, "chin") 得1

+   -strcmp(st, "china") 得0

+   -strcmp(st, "0123456789") 得1

+   -strcmp("this is a string", "this’s a string")得-1

+   直接用运算符<,==,>比较字符串，则是在比较地址值
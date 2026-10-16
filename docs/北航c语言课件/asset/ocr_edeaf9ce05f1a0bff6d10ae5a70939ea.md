说明：(1)指针变量与数组名的区别：

Difference between the pointer variable and the array name.

指针变量是地址变量，其内容可以在程序运行过程中被改变。

数组名是地址常量，一旦被定义，它的地址就不能再改变了。

The pointer variable is an *address variable*, and the array name is an *address constant*.

例如：`int i, *p, a[6];`　则：`p=&i;`　√

~~a=&i~~；~~a++~~；~~a=i~~；不能给常量赋值
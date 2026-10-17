cout<<*(int*)p; //正确

char *c="abc" ;

p=c;//c=p则不可以

cout<<p;//错误

cout<<(char*)p; //正确

void **pp;

pp=p; //正确

char *cc;

cc=p; //错误

# 四．常量类型const

+   • 一般情况下，const和define在定义符号常量时功能几乎是一样的。

例： const float pi=3.14; //限定pi为float型的常量；

    const int SIZE=100; //限定SIZE为int型的常量；

+   • 但在定义指针变量时，const却有不同的地方。例如：

+   (1) const char *pc=" abcd" ;// 指向串常量的指针

//限定指针pc只能指向一个串常量，一旦赋值，它所指的值不能再修改。

但是可以把pc指向其他内存单元。即pc是一个可以用来读取值而不能用来修改

值的指针（只读指针）。

+   (2)char *const pc=" abcd" ;// 指向串的常量指针,pc指向的值可以被
+   
+   修改，但是不能把pc指向其他内存单元。

+   (3)const char *const pc=" abcd" //（1），（2）的综合

+   (4)另外：赋值时注意：

pc[1]=' s' //错

pc=" xyz" //正确
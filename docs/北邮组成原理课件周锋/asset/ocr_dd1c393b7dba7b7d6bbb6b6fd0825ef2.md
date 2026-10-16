# 四、格式化读／写——`fscanf()`和`fprintf()`函数

`fscanf()`和`fprintf()`函数，用于ASCII文件的处理。

其功能与`scanf()`和`printf()`函数相似，区别在于：`fscanf()`和`fprintf()`函数的操作对象是指定文件，而`scanf()`和`printf()`函数的操作对象是标准输入输出文件。

+   1、`int fscanf(FILE * stream, const char * format, 输入变量首地址表);` /*读文件*/

如：`fscanf(fPtr, "%d,%f", &i, &f);`

`fscanf(stdin, const char * format, 输入变量首地址表)`

等价于

`scanf(const char * format, 输入变量首地址表)`
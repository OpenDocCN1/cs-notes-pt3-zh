# 打开文件

+   - 函数原型
+     `FILE* fopen ( const char* filename, const char* mode );`

+   - 调用方式
+     `fp = fopen( filename , mode );`

+   - **filename** 是一个字符串，具体给出要打开的文件的文件名；

+   - **mode** 也是一个字符串，具体给出文件的打开模式，表12-1列出各种打开模式；

+   - **fp** 是文件指针变量，以后程序中使用该指针变量标识由文件名给出的文件。
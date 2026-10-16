
# 处理文件注意事项

- 文件操作是事故多发区
  - 文件不存在
  - 文件已存在
  - 磁盘满
  - 写一个只读文件，读一个只写文件
  - 设备损坏
- 在事故发生时，程序必须能自如应对，这就需要错误处理技术

# 错误处理

- ferror()函数
  - ferror(fp);
  - 检查输入输出函数的调用是否正确，返回非0值，表示出错。
  - 调用一个输入输出函数后，立即检查ferror函数的值

# 错误处理判断和策略

| 函数 | 当返回值 | 常用策略 |
|---|---|---|
| fopen() | ==NULL | 转移错误处理流程 |
| fprintf() | <0 |  |
| fputc()、putc() | ==EOF |  |
| fwrite() | <nmem b |  |
| fputs() | ==EOF |  |
| fgets() | ==NULL | 停止再次调用该函数，继续下一步 |
| fscanf() | ==0 或 ==EOF |  |
| fgetc()、getc() | ==EOF |  |
| fread() | <nmem b |  |
| fclose()、fflush() | ==EOF | 忽略 |

# 两种方式的区别

- open族的功能一般由OS直接提供，其使用方式也比较具有通用性，在各种语言里基本一样
- fopen族的函数系包装了open族的函数，提供更强大的功能，但是效率略微
- open族通常情况下直接反映文件的真实情况，因为它的操作都不假定文件的任何结构
- fopen族比较适合处理文本文件，或者结构单一的文件。会为了以处理的方式而改变一些内容

# C语言的文件操作实例-源码1

```c
int CopyFile(const char* srcName,
    const char* dstName){
    FILE* fpSrc = NULL;
    FILE* fpDst = NULL;
    int ch, rval=1;
    fpSrc = fopen(srcName, "rb");
    if(fpSrc == NULL)
        goto ERROR;
    fpDst = fopen(dstName, "wb");
    if(fpDst == NULL)
        goto ERROR;
    while((ch=fgetc(fpSrc))!=EOF){
        if(fputc(ch, fpDst)==EOF)
            goto ERROR;
    }
```

```c
fflush(fpDst);
goto EXIT;
ERROR:
    rval=0;
EXIT:
    if(fpSrc != NULL)
        fclose(fpSrc);
    if(fpDst != NULL)
        fclose(fpDst);
    return rval;
```
```

# C语言的文件操作·源码2

```
1 main(int argc, char *argv[])
2 {
3 if (argc != 3){
4 printf("too few parameters!\n");
5 exit(0);
6 }
7 if (CopyFile(argv[1], argv[2])){
8 printf("Copy succeed.\n");
9 }
10 else{
11 perror("Copy failed");
12 }
13 }
```

谢谢大家，欢迎提问！

# C语言总复习

# 数据类型

- 关键字
- 标识符
  - 命名规则
- 运算符
  - 自增运算算法
- 类型转换
  - 自动转换
  - 强制转换

# 简单C程序设计

- scanf()
  - 别忘了地址运算符
- printf()
  - 格式化信息输出，数字控制宽度

# 程序的控制结构

- 判断
  - If else
  - Switch
- 循环
  - For , while, for while
- Break, continue
- 语句块
  - 单行语句

# 函数

- 函数的声明和定义
- 形参和实参
- 变量的作用域
- 预处理指令
- #define 的潜在危险
- 返回值
- 需要返回多个值的时候怎么办？

# 数组

- 数组的定义
  - 数组名就是地址常量
  - 数组作为函数参数
    - “把” 概念的推广
  - 二维数组
  - 数组下标和越界

# 指针1

- 指针定义
- 地址运算符和指针运算符
- 指针的用处
- 改变实参
- 效率
- 构建数据结构
- 从函数传回多个数据

# 指针2

- 指针的算数运算
- 指针的关系运算
- 数组和指针
- 指针数组
- 命令行参数
  - argv

# 字符串

- 指针表示法
- 数组标示法
- 不能把字符串当成一个整体变量
- 字符串相关函数

# 结构体数组

- 结构体声明和定义
- 结构体成员的访问
  - 变量
  - 指针

# 文件操作

- 打开一个文件
  - R+ w+
- 循环访问文件
  - Fgetc
  - Fgets

# 泄露一道考题

- 评价你的老师，两条主要的优点，两条主要的缺点

# 未来的的建议1

- Google+英文
  - 拷贝错误信息
  - 构造字符串
- 调试器
  - 发现错误
  - 验证程序
  - 理解别人的意图

# 未来的的建议2

- 任务驱动
- 商用项目
- ACM和学生俱乐部
- 开源项目
- 自己动手...

# 未来的的建议3

- 学点语法，关注思想，
- 对象
- Kiss
- 接口
- ……

# 未来的的建议4

- 增加内功
  - 数据结构
  - 算法
  - 操作系统
- 掌握语言
  - C
  - C++ java
  - python

- Ambitious, active, aggressive
- 路虽迷，渐行渐至。事虽小，不为不成！

# 我的联系方式

- 乐学网
- Zhaoyan.hrb@gmail.com
- QQ: 1619604531
- Mobile phone: 18686836933

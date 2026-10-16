# 2.命令行参数的传递示例

例8.11 分析下列程序，指出其执行结果，该程序命名为exam.c，经编译连接后生成的可执行程序为exam.exe

```
#include <stdio.h>
main (int argc, char * argv[])
{ int i=0;
    printf("argc=%d\n",argc);
    while (argc >=1)
    { printf("\n参数%d: %s",i,*argv);
        i++; argc--; argv++;
    }
}
```

若运行时的命令行输入的是:
exam Turbo_c C++ Vc

输出结果:
argc=4
参数0: exam
参数1: Turbo_c
参数2: C++
参数3: Vc

程序开始运行后，系统将命令行中字符串个数送argc,将四个字符串实参：exam、Turbo_c、C++、Vc的首地址分别传给字符指针数组元素argv[0]、argv[1]、argv[2]、argv[3]。
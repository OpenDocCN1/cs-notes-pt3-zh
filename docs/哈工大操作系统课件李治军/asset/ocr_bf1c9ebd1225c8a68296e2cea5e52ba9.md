# 命令行是怎么回事？

cst:/home/lizhijun$ ./output "hello"
ECHO:hello

# 命令是什么？命令输入后发生了什么？

```
#include <stdio.h>
int main(int argc, char * argv[])
{ printf("ECHO:%s\n", argv[1]); }
```

命令，一段程序而已

shell也是一段程序: 即/bin/sh

```
gcc -o output output.c
```

./output "hello"

命令是什么？一个用
C语言写的程序而已

```
int main(int argc, char * argv[])
{ char cmd[20];
while(1) { scanf("%s", cmd);
if(!fork()) {exec(cmd);}
else {wait();} } //while(1)
}
```
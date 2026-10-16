# 例7-12 编程序输出命令行的参数内容

```
#include <stdio.h>
void main(int argc,char* argv[]){
    printf("argc=%d\n",argc);
    printf("command name:%s\n", argv[0]);
    for(int i=1;i<argc;i++)
        printf("Argument %d: %s \n", i, argv[i]);
}
```

程序运行结果为：
argc=5
commard name:tt
Argument 1:se.txt
Argument 2:hope
Argument 3:ee
Argument 4:efe

如果执行该程序，在DOS下键入命令行：
C> tt se.txt hope ee efe <CR>
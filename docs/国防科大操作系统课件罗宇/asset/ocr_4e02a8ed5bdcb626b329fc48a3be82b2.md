# 能轻松完成上一题的同学

用VC调试两个程序中的一个，并试着解释现象：

```
#include "stdafx.h"
#include <stdlib.h>
void SayHello(void) {
    printf("Hello World!\n");
    exit(0);
}
void __stdcall BadBoy(void) {
    int a = 0x1234;
    int *s = &a;
    *(s+2) = (int)SayHello;
}
int main(void){
    BadBoy();
    return 0;
}
```

```
#include "stdafx.h"
#include <stdlib.h>
void __stdcall SayHello(void){
    printf("Hello World!\n");
    exit(0);
}
void __stdcall BadBoy(void){
    unsigned int a[1];
    int i;
    for (i=0; i<3; i++)
        a[i] = (unsigned int)SayHello;
}
int main(void) {
    BadBoy();
    return 0;
}
```
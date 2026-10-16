# 将关于write的故事完整的讲完...

_syscall3表示有3个参数

```
在linux/include/unistd.h中
#define _syscall3(type,name,atype,a,btype,b,ctype,c)\ntype name(atype a, btype b, ctype c) \
{ long __res;\
__asm__ volatile("int 0x80":"=a"(__res):"0"(__NR_##name),\n"b"((long)(a)),"c"((long)(b)),"d"((long)(c))); if(__res>=0) return (type)__res; errno=-__res; return -1;}
```

显然，__NR_write是系统调用号，放在eax中

```
在linux/include/unistd.h中
#define __NR_write 4 //一堆连续正整数(数组下标，函数表索引)
```

同时eax也存放返回值，ebx，ecx，edx存放3个参数
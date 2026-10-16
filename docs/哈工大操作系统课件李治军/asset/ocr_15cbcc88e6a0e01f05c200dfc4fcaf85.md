# fd=1的filp从哪里来？

因为是被current指向，所以是从fork中来

```
int copy_process(...){\n*p = *current;\nfor (i=0; i<NR_OPEN;i++)\n    if ((f=p->filp[i])) f->f_count++;
```

显然是拷贝来的，那么是谁一开始打开的？

shell进程启动了whoami命令，shell是其父进程

```
void main(void)\n{ if(!fork()){ init(); } }
```

```
void init(void)\n{open("/dev/tty0",O_RDWR,0);dup(0);dup(0);\nexecve("/bin/sh",argv,envp) }
```

![](bbox=[0.92, 0.72, 0.98, 0.92])
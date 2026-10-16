# execl() 加载并执行新程序

![](bbox=[0.01, 0.14, 0.95, 0.83])

proc结构
p_pid=9
p_ppid=5
user结构

```
pid=fork();
if(pid == 0) /*不成立*/
{
    execl("p",0);
}else{
    /*父进程代码*/
}
...
```

父进程

proc结构
p_pid=12
p_ppid=9
user结构

```
pid=fork();
if(pid == 0) /*成立*/
{
    execl("p",0);
}else{
    /*父进程代码*/
}
...
```

子进程
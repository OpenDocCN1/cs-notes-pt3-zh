# 多进程图像从启动开始到关机结束

+   - main中的fork()创建了第1个进程
+     - init执行了shell(Windows桌面)
+   - shell再启动其他进程

```
if(!fork()){init();}
```

```
int main(int argc, char * argv[]) {
    while(1) { scanf("%s", cmd);
        if(!fork()) {exec(cmd);} wait(); }
}
```

![](bbox=[0.057, 0.638, 0.626, 0.856])

![](bbox=[0.878, 0.14, 0.952, 0.258])
```
```c
main() {
    while(TRUE) {
        Read();
        Decompress();
        Play();
    }
}
Read() {...}
Decompress() {...}
Play() {...}
```
```

# 问题：

+   - 播放出来的声音能否连续？
+   - 各个函数之间不是并发执行，影响资源的使用效率；
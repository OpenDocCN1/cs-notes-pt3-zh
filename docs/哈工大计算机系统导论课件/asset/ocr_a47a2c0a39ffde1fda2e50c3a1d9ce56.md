# 系统调用错误的处理

+   - 当Linux系统级函数遇到错误时，通常返回-1并设置全局整数变量 `errno` 来标示出错原因。
+   - 硬性规定:
+     - 必须检查每个系统级函数的返回状态
+     - 只有少数是返回空的函数
+   - Example:

```
if ((pid = fork()) < 0) {
    fprintf(stderr, "fork error: %s\n", strerror(errno));
    exit(0);
}
```
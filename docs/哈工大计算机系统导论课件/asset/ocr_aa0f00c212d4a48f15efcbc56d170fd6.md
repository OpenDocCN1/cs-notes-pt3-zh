# # 链接时打桩

```
```text
linux> make intl
gcc -Wall -DLINKTIME -c mymalloc.c
gcc -Wall -c int.c
gcc -Wall -Wl,--wrap,malloc -Wl,--wrap,free -o intl int.o mymalloc.o
linux> make runl
./intl
malloc(32) = 0x1aa0010
free(0x1aa0010)
linux>
```
```

+   - **“--Wl”标志将参数传递给链接器，将每个逗号替换为空格**
+   - **“--wrap,malloc”参数** 指示链接器以一种特殊的方式解析引用：
+     - 对 `malloc` 的引用，必须被解析为 `__wrap_malloc`
+     - 对 `__real_malloc` 必须被解析为 `malloc`
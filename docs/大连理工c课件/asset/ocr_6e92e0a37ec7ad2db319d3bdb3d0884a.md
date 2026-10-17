# 9.4 文件流

# 文件指针

ios::beg

ios::cur

ios::end

0  1  2  3  4  5

n-1

文件结束

```
enum ios::seek_dir { beg = 0; cur = 1; end = 2 };
```

+   **ios::seek_dir** 值：
+   
+   - **cur**　相对于当前读指针所指定的当前位置
+   - **beg**　相对于流的开始位置
+   - **end**　相对于流的结尾处
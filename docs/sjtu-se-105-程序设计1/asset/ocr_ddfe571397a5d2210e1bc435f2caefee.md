# 符号流

+   - 自定义类型Token_stream
+     - get()和putback()

```
class Token_stream {
public:
    Token_stream(); //创建一个从cin读入的 Token_stream
    Token get();     // 获取一个符号 (get() 是在其他地方定义的)
    void putback(Token t);  // 将一个符号放回
private:
    bool full;       // 这个符号在缓存中吗？
    Token buffer;    // 我们将使用putback()放回的符号放在这里
};
```
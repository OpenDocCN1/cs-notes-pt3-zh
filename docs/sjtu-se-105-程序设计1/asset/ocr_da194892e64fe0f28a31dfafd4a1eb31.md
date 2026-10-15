# 技术细节：覆盖

+   - 如果想覆盖一个虚函数，你需要：
+     - 一个虚函数
+     - 完全相同的名称
+     - 完全相同的类型

```
struct B {
    void f1(); // not virtual
    void f2(char);
    void f3(char) const;
    void f4(int);
};
```

```
struct D : B {
    void f1();        // doesn't override
    void f2(int);     // doesn't override
    void f3(char);    // doesn't override
    void f4(int);     // overrides
};
```
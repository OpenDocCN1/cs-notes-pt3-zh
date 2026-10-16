# 14.5 不是错误的异常

+   - 有些异常是预期内的，簇改变捕捉到也不会对程序行为产生不良影响

```
void f(Queue<X>& q) {
    try {
        for(;;) {
            X x = q.get();
            // ...
        }
    }
    catch(Queue<X>::Empty) {
        return;
    }
}
```

换一种看法，我们也可以为异常处理机制根本不是另一种控制结构。

需要注意的是，异常处理是一种结构化更差的机制，通常在实际应用中效率也更低。

# 示例

+   - 有时候，采用异常作为返回方式是一种很优雅的技术
+   - 任何有助于维持一套关于一个错误是什么以及它应该如何处理的清晰模型，都是非常必要的

```
void find(Tree* p, const string& s) {
    if(s==p->str) throw p;
    if(p->left) find(p->left,s);
    if(p->right) find(p->right,s);
}

void find(Tree* p,
          const string& s) {
    try { find(p,s); }
    catch(Tree* q) {
        return q;
    }
    return 0;
}
```

# 14.6 异常的描述

+   - 将可能抛出的异常集合称作为函数声明的一部分是有价值的，它可以有效的为调用者提供一种保证
+   
+     ```cpp
+     void f(int a) throw(x2,x3);
+     // 保证函数只会抛出x2、x3以及从这些类型派生的异常
+     ```
+   
+   - 若函数不遵循自己作出的保证，这个全图将会被转换为一个对std::unexpected()的调用，其默认意义是std::terminate()，通常将被转为对abort()的调用

# 异常的描述

```
void f() throw(x2,x3)
{/*...*/}

等价于
void f()
try
{
    // ...
}
catch(x2){throw;}
catch(x3){throw;}
catch(...){
    std::unexpected();
}
```

这里最重要的优点在于函数的声明贴于界面，而强制函数要声明异常可以看到的。

另外，函数的定义一般是不可用的东西，即使有编译，也不会理经常去查。

最后，带有异常描述的函数也能手工写出的等价版本要更漂亮。
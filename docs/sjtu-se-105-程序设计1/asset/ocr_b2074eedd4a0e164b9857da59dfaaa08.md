+   - destroy函数：
+     ```cpp
+     template <class Type> void Queue<Type>:: destroy()
+     {
+         while (!empty())
+             pop();
+     }
+     ```
+   - 用名为Type的类型形参定义一个函数模板；
+   - 它返回void
+   - 它是在类模板Queue<Type>的作用域中
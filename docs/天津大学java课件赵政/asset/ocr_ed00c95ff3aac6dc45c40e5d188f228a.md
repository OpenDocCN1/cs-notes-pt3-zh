# # 8.8.1 使用final阻止重写

+   - 声明成final的方法不能被重载
+   
+   ```java
+   class A {
+       final void meth() {
+           System.out.println("This is a final method.");
+       }
+   }
+   
+   class B extends A {
+       void meth() {   // ERROR! Can't override. 编译错误
+           System.out.println("Illegal!");
+       }
+   }
+   ```

+   - final方法可以形成内嵌代码（inline）。

+   - 早期绑定 （early binding）。
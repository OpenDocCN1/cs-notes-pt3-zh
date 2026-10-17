# # 9.4.2 实现接口

+   - 接口被定义后，一个或多个类可以实现该接口。
+   - 在类定义中包括implements 子句，然后创建接口定义的方法。
+   - implements 类的一般形式如下：
+     ```java
+     access class classname [extends superclass]
+     [implements interface [,interface...]] {
+     // access是public，或无修饰符
+     // 如果一个类实现多个接口，这些接口被逗号分隔
+     // class-body //方法必须声明成public。
+     //方法的类型须与接口定义类型相匹配。
+     }
+     ```
# # 利用Scanner类中的方法输入数据

+   - 使用java.util.Scanner,建立一个Scanner对象,就可以输入数据了。
+     ```java
+     import java.util.Scanner;
+     Scanner in=new Scanner(System.in);
+     ```

+   - 输入各类数据：
+     ```java
+     short a;int b;long c;float d;double e;String f,g;
+     a=in.nextShort();
+     b=in.nextInt();
+     c=in.nextLong();
+     d=in.nextFloat();
+     e=in.nextDouble();
+     f=in.next();
+     g=in.nextLine();
+     ```
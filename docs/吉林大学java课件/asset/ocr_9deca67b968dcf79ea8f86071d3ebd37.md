# # 如何使用包中的类

```
```java
import mypackage.Calculate;
class PackageDemo {
public static void main(String ags[]){
Calculate c=new Calculate();
System.out.print(c.volume(3f, 4f, 4));
//System.out.println(c.mul(3, 4));//非法
//System.out.println(c.add(5, 6)); //非法
}
}
```
```

注意：
1 该类的编译和运行需要设置环境变量classpath。
2 如何设置？ 设置Calculate类所属的包的所在子目录。
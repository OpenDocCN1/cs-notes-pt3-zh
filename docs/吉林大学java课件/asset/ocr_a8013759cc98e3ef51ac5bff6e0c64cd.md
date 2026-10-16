# 匹配任意类型的通配符

在开发中对象的引用传递是最常见的，但是如果在泛型类的操作中，在进行引用传递的时候泛型类型必须匹配才可以传递，否则是无法传递的。

```
public class GenericsDemo12 {
    public static void main(String[] args) {
        Info<String> i = new Info<String>();    // 指定Object为泛型类型
        i.setVar("李兴华");    // 设置字符串
        fun(i);    // 错误, 无法传递
    }
    public static void fun(Info<Object> temp){
        // Object泛型类型的Info对象
        System.out.println("内容: " + temp);
    }
}
```
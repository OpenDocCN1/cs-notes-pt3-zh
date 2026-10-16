# 子类同时继承抽象类和实现接口

```
interface A{ // 定义接口A
    public String AUTHOR = "李兴华"; // 定义全局常量
    public void print(); // 定义抽象方法
    public String getInfo(); // 定义抽象方法
}
abstract class B{ // 定义抽象类 B
    public abstract void say();
}
class X extends B implements A{ // 子类同时实现接口
    public void say() { // 覆盖抽象类B中的抽象方法
        System.out.println("Hello World!!!");
    }
    public String getInfo() { // 覆盖接口A中的抽象方法
        return "HELLO";
    }
    public void print() { // 覆盖接口A中的抽象方法
        System.out.println("作者: " + AUTHOR);
    }
}
```
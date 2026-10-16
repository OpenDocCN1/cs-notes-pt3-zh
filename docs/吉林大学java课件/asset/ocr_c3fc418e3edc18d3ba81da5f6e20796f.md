# 封装的实现

为属性封装： private 属性类型 属性名称；
为方法封装： private 方法返回值 方法名称(参数列表){}

```
class Person {
    private String name;            // 声明姓名属性
    private int age;                // 声明年龄属性
    public void tell() {            // 取得信息的方法
        System.out.println("姓名: " + name + ", 年龄: " + age);
    }
}
public class EncDemo02 {
    public static void main(String args[]) {
        Person per = new Person();
        per.name = "张三";    // 错误, 无法访问封装属性
        per.age = -30;        // 错误, 无法访问封装属性
        per.tell();
    }
}
```
# 对象的创建及使用

| 类名 对象名称 = null; // 声明对象 | 对象名称 = new 类名(); // 实例化对象 |
| 类名 对象名称 = new 类名(); |  |

```
class Person {
    String name;
    int age;
    public void tell() {
        System.out.println("姓名: " + name + ", 年龄: " + age);
    }
}
public class ClassDemo02 {
    public static void main(String args[]){
        Person per = new Person();
    }
}
```
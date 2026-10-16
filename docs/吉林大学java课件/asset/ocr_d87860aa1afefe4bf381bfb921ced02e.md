# 错误的方法覆盖

如果现在被子类覆盖的方法权限缩小的话，则在编译时将出现错误提示。

```
class Person{
    public void print(){
        // 定义一个默认访问权限的方法
        System.out.println("Person --> void print(){}");
    }
}
class Student extends Person{
    // 定义一个子类继承Person类
    void print(){
        // 覆盖父类中的方法，但缩小了权限，错误
        System.out.println("Student --> void print(){}");
    }
}
```
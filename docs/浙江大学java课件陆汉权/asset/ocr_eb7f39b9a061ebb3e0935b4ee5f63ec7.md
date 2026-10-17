# 例7-2--利用super访问父类成员

```
class Person2 {
    protected String name;
    protected int age;

    public Person2(String na, int ag) { // 构造方法
        name=na;
        age=ag;
    }

    public void print() { // print方法
        System.out.println("Parent:Name="+name+"
Age="+age);
    }
} // 类 Person2结束
```
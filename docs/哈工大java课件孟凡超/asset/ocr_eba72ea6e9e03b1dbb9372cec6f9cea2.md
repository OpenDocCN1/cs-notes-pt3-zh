# 5.3 this引用

在Java中，如果在类的成员方法中访问类的成员变量，可以使用关键字 this 指明要操作的对象。

```
public class Student {
    String name;
    int age;
    public Student(String name, int age){
        this.name=name;
        this.age=age;
    }
    public Student(String name){
        this(name,20);
    }
    public Student(){
        this("Unknown");
    }
    /**
     * @param args
     */
    public static void main(String[] args) {
        // TODO Auto-generated method stub
        Student s1=new Student();
        System.out.println("name="+s1.name+" age="+s1.age);
        
        Student s2=new Student("Zhangsan",24);
        System.out.println("name="+s2.name+" age="+s2.age);
        
        Student s3=new Student("lisi");
        System.out.println("name="+s3.name+" age="+s3.age);
    }
}
```
# 使用super调用父类中的指定构造方法

```
class Person {
    private String name;                 // 定义类Person
    private int age;                     // 定义name属性
    public Person(String name,int age){  // 通过构造方法设置name和age
        this.setName(name);              // 设置name属性内容
        this.setAge(age);                // 设置age属性内容
    }
    setter, getter
    public String getInfo(){             // 信息输出
        return "姓名：" + this.getName() + "; 年龄：" + this.getAge();
    }
}
class Student extends Person {           // Student是Person的子类，扩展父类的功能
    private String school;               // 新定义的属性school
    public Student(String name,int age,String school){
        super(name,age);                 // 指定调用父类中的构造方法
        this.setSchool(school);
    }
    setter, getter
    public String getInfo(){             // 覆写父类中的方法
        return super.getInfo() +
                "; 学校：" + this.getSchool(); // 扩充父类的方法
    }
}
```
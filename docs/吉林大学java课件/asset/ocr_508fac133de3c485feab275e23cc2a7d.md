# 隐含的语句

+   对于以上的代码实际在子类的构造函数中隐含了一个super()的语法

```
class Student extends Person {    // Student是Person的子类, 扩展父类的功能
    private String school;                // 新定义的属性school
    public Student() {
        super() ;                          // 加与不加此语句效果一致
        System.out.println("子类Student中的构造.") ; // 子类的构造方法
    }
    public String getSchool() {    // 取得school属性
        return school;
    }
    public void setSchool(String school) { // 设置school属性
        this.school = school;
    }
}
```
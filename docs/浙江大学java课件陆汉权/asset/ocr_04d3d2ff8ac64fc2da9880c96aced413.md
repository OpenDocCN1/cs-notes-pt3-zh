# # Java实例——（续）

```
public void print_p() {
    System.out.println("Name:"+name+"  Age:"+age);
}
} 类Person1结束
```

```
public class Teacher1 extends Person1 { // 子类派生于父类
    protected String department; // 定义了成员变量 系部

    public Teacher1(String na, int ag, String de) {
        setName(na);
        setAge(ag);
        department=de;
    }
```
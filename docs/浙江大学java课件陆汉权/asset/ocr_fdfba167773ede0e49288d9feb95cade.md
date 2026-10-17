```
```java
public static void main(String args[]) {
    Student zhang;  //声明并创建zhang对象
    zhang=new Student("张三","西安市兴庆路1号",3);
    Student wang;  //声明并创建wang对象
    wang=new Student("王五","西安市翠华路12号",4);
    System.out.println(zhang.name+zhang.address+zhang.grade);
    System.out.println(wang.name+wang.address+wang.grade);
}
}
```
```
```
```java
public class Statistic {

    public static void main(String args[]) {
        Course c1,c2;  // 定义Course对象c1、c2
        c1=new Course("210",90);  // 学号210，成绩90
        Course.summarize(90);
        System.out.println("sum="+c1.sum);
        c2=new Course("300",80);  // 学号300，成绩80
        c2.summarize(80);
        System.out.println("sum="+Course.sum); // 输出累加和
    }
} // 类Statistic结束
```
```
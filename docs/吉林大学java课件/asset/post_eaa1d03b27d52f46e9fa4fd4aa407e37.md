
## 成员变量和局部变量

- 变量声明的位置决定变量作用域
- 变量作用域确定可在程序中按变量名访问该变量的区域

```java
//...
for(int a = 0; a < 4; a++) {
    System.out.println("hello");
}
System.out.println( a );
//...
```

代码错误，a的作用域仅在for循环中

谁能使用这些变量？

```
public class AutoLion{

变量1类型 变量1;
变量2类型 变量2;
变量3类型 变量3;

public 返回类型 方法1(){
变量4类型 变量4;
}

public 返回类型 方法2(){
变量5类型 变量5;
}
}
```

成员变量

AutoLion类的方法

方法1

局部变量

方法2

## 常见错误

```
public class Test {
    int score1 = 88;
    int score2 = 98;
    public void calcAvg() {
        int avg = (score1 + score2)/2;
    }
    public void showAvg(){
        System.out.println("平均分是： " + avg);
    }
}
```

局部变量超出其作用域后不可用！

## 成员变量和局部变量的区别

- 作用域不同
  - 局部变量的作用域仅限于定义它的方法
  - 成员变量的作用域在整个类内部都是可见的

- 初始值不同
  - Java会给成员变量一个初始值
  - Java不会给局部变量赋予初始值

注意
在同一个方法中，不允许有同名局部变量
在不同的方法中，可以有同名局部变量

在同一个类中，成员变量和局部变量同名时，局部变量具有更高的优先级

## 小结

说出以下代码的运行结果

```
public class Test {
    public int num;
    public void calc(int num1,int num2){
        System.out.println(num+num2);
    }
    public static void main(String[] args) {
        Test test = new Test();
        test.num=10;
        test.calc(11,3);
    }
}
```

14

## 面向对象（基础）
—— 封装性

## 封装（封装的概念本身很好理解，意思就是把一堆东东装起来）

第一个问题是：我们要封装什么？

这个问题很好回答，封装当然是封装不想让别人知道或者看到的东东了。

例如：

- 你的身家。。。。。。
- 漂亮MM的年龄。。。。。 。
- 富二代的女朋友数。。。。。 。
- 明星是否整过容。。。。。 。
- 你是如何赚到100万的（想想什么样的赚钱方法不想让人知？）。。。。。
- 你是如何消磨时间的（想想什么样的消磨时间方法不想让人知道？）。。。。。

站在面向对象的角度来说，封装就是“类”的一个功能，你可以封装“类”的属性（比如身家、年龄等），也可以封装“类”的方法（比如说如何赚钱、如何消磨时间），也就是说，面向对象通过“类”来实现封装。

## 为什么要有封装？（属性）

> 封装属性的主要原因是为了“保护隐私”，因为有“隐私”，所以要“封装”。如果没有封装，你的隐私就暴露在所有人的面前了，别人也可以控制你的隐私，那样将是非常危险的。

而面向对象的类封装了属性后，对属性的修改只能通过类的方法进行，一来不会暴露内部的具体属性，二来对属性的操作都是统一的，不会出现乱改的情况。

## 封装的实现

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

## 加入验证

- 可以在setter方法中对设置的内容进行验证

```
public void setAge(int a) {
    if (a >= 0 && a < 150) {
        age = a;
    }
}
// 设置年龄
// 在此处加上验证代码
```

## 例子

```
package com.oo.java;
/**
 * 普通人
 */
public class Person {
    private String _name; //姓名
    private Integer _money; //金钱
    public String getName() {
        return _name;
    }
    public Boolean pay(Integer money){
        //付款的逻辑由Person自己控制，例如判断当前的钱是否够支付
        if( money > _money){
            return false;
        }
        _money -= money;
        return true;
    }
}
```

## 例子

```
package com.oo.java;
/**
 * 收银员
 */
public class Cashier {
    public Boolean get(Person person, Integer money){
        Boolean result = person.pay(money); //收银员只需要调用Person的pay方法，无需知道Person当前有多少钱
        if( result ){
            System.out.println(person.getName() + " 付款成功，共 " + money + " 块");
        }
        else{
            System.out.println(person.getName() + " 付款失败");
        }
        return result;
    }
}
```

## 例子

```
package com.oo.java;

/**
 * 小偷
 */
public class Thief {

    public Boolean stole(Person person){

        //小偷想直接访问Person的money，但这样做不允许，编译出错
        System.out.println("偷了 " + person.getName() +" " + person._money + " 块\n");
        person._money = 0;

        //虽然小偷这个类语法上也可以直接调用Person的pay方法，
        //但Person的pay方法里面可以做很多的校验功能来让这样的调用返回失败
        person.pay(50);
    }
}
```

## 本章目标

- 掌握构造方法的概念及调用时机
- 掌握构造方法的重载
- 掌握匿名对象的使用

## 构造方法

- ◇ 对象的产生格式:
  - ✧ 类名称 对象名称 = new 类名称()

因为有“()”，所以表示的是一个方法
这实际上就是一个构造方法

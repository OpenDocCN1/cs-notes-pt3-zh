
## 例 P121　public 和 private 对访问的作用

```java
/* This program demonstrates the difference between
public and private.
*/
class Test {
    int a;                 // default access
    public int b;          // public access
    private int c;         // private access
    // methods to access c
    void setc(int i) {     // set c's value
        c = i;
    }
    int getc() {           // get c's value
        return c;
    }
}
```

![img](img/489adce8323ca3a7b0e9fe701e6e665c_301_0.png)

```java
class AccessTest {
    public static void main(String args[]) {
        Test ob = new Test();
        // These are OK, a and b may be accessed directly
        ob.a = 10;
        ob.b = 20;
        // This is not OK and will cause an error
        // ob.c = 100; // Error!
        // You must access c through its methods
        ob.setc(100); // OK
        System.out.println("a, b, and c: " + ob.a + " " +
                           ob.b + " " + ob.getc());
    }
}
```

Ans:

a, b, and c: 10 20 100

## 例 P122　Stack 类的改进版本

```java
// This class defines an integer stack that can hold 10 values.
class Stack {
  /* Now, both stck and tos are private. This means
     that they cannot be accidentally or maliciously
     altered in a way that would be harmful to the stack.
  */
  private int stck[] = new int[10]; // 堆栈 stck 和堆栈顶下标 tos,
  private int tos;                  // 都被指定为private

  // Initialize top-of-stack
  Stack() { tos = -1; }

  // Push an item onto the stack
  void push(int item) {              // push()或pop()才能访问或改变
    if(tos==9)
      System.out.println("Stack is full.");
    else
      stck[++tos] = item;
  }

  // Pop an item from the stack
  int pop() {
    if(tos < 0) {
        System.out.println("Stack underflow.");
        return 0;
    }
    else
        return stck[tos--];
  }
}
```

```java
class TestStack {
public static void main(String args[]) {
Stack mystack1 = new Stack();
Stack mystack2 = new Stack();
// push some numbers onto the stack
for(int i=0; i<10; i++) mystack1.push(i);
for(int i=10; i<20; i++) mystack2.push(i);
// pop those numbers off the stack
System.out.println("Stack in mystack1:");
for(int i=0; i<10; i++)
System.out.println(mystack1.pop());
System.out.println("Stack in mystack2:");
for(int i=0; i<10; i++)
System.out.println(mystack2.pop());
// these statements are not legal
// mystack1.tos = -2;
// mystack2.stck[3] = 100;
}
}
```

## 7.7 理解 static

- 一个类成员的使用完全独立于该类的任何对象。
- 在成员的声明前面加上关键字 static（静态的）就能创建这样的成员。
- 如果一个成员被声明为 static，它就能够在它的类的任何对象创建之前被访问，而不必引用任何对象。
- static 成员的最常见的例子是main()。
- 声明为 static 的变量实质上就是全局变量。该类所有的实例变量共用同一个 static 变量。

声明为 static 的方法有以下几条限制：

- 它们仅能调用其他的 static 方法。
- 它们只能访问 static 数据。
- 它们不能以任何方式引用 this 或 super。

- 初始化 static 变量，可以声明一个 static 块，static 块仅在该类被加载时执行一次。

## 例 P124　static方法，static变量，static初始化块

```java
// Demonstrate static variables, methods, and blocks.
class UseStatic {
    static int a = 3;
    static int b;
    static void meth(int x) {
        System.out.println("x = " + x);
        System.out.println("a = " + a);
        System.out.println("b = " + b);
    }
    static {
        System.out.println("Static block initialized.");
        b = a * 4;
    }
    public static void main(String args[]) {
        meth(42);
    }
}
```

Ans:

Static block initialized.
x = 42
a = 3
b = 12

// 一旦UseStatic被装载,所有Static语句被执行,
// 执行顺序如下:
// a->3, static块执行(打印一条消息), b->a*4=12
// ->main()->meth(42)
// 3个println () ->a, ->b, ->x 。

## 例 P125　static方法和static变量b在它们的类之外被访问

```java
// static 方法和变量能独立于任何对象而被使用。
// 你只要在类的名字后面加点号运算符即可。
class StaticDemo {
    static int a = 42;
    static int b = 99;
    static void callme() {
        System.out.println("a = " + a);
    }
}
class StaticByName {
    public static void main(String args[]) {
        StaticDemo.callme();
        System.out.println("b = " + StaticDemo.b);
    }
}
```

![img](img/489adce8323ca3a7b0e9fe701e6e665c_310_0.png)

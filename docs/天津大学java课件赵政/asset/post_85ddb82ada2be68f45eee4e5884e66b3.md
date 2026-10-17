

## 8.3 创建多级类层次

- 可以建立包含任意多层继承的类层次。
- 例如，C 是 B 的一个子类，而 B 又是 A 的一个子类。
- 每个子类继承它的所有超类的属性。
- super() 总是引用子类最接近的超类的构造函数。
- Shipment 中 super() 调用了 BoxWeight 的构造函数。BoxWeight 中的 super() 调用了 Box 中的构造函数。
- 在类层次结构中，如果超类构造函数需要参数，那么不论子类它自己需不需要参数，所有子类必须向上传递这些参数。

### 例 P142

### Box -> BoxWeight -> Shipment

```java
// Extend BoxWeight to include shipping costs.
// Start with Box.
class Box {
    private double width;
    private double height;
    private double depth;
    // construct clone of an object
    Box(Box ob) { // pass object to constructor
        width = ob.width;
        height = ob.height;
        depth = ob.depth;
    }
    // constructor used when all dimensions specified
    Box(double w, double h, double d) {
        width = w;
        height = h;
        depth = d;
    }
    // constructor used when no dimensions specified
    Box() {
        width = -1; // use -1 to indicate
        height = -1; // an uninitialized
        depth = -1; // box
    }
    // constructor used when cube is created
    Box(double len) {
        width = height = depth = len;
    }
    // compute and return volume
    double volume() {
        return width * height * depth;
    }
}
```

```java
// Add weight.
class BoxWeight extends Box {
    double weight; // weight of box
    // construct clone of an object
    BoxWeight(BoxWeight ob) { // pass object to constructor
        super(ob);
        weight = ob.weight;
    }
    // constructor when all parameters are specified
    BoxWeight(double w, double h, double d, double m) {
        super(w, h, d); // call superclass constructor
        weight = m;
    }
    // default constructor
    BoxWeight() {
        super();
        weight = -1;
    }
    // constructor used when cube is created
    BoxWeight(double len, double m) {
        super(len);
        weight = m;
    }
}
```

```java
// Add shipping costs
class Shipment extends BoxWeight {
    double cost;
    // construct clone of an object
    Shipment(Shipment ob) { // pass object to constructor
        super(ob);
        cost = ob.cost;
    }
    // constructor when all parameters are specified
    Shipment(double w, double h, double d,
             double m, double c) {
        super(w, h, d, m); // call superclass constructor
        cost = c;
    }
    // default constructor
    Shipment() {
        super();
        cost = -1;
    }
    // constructor used when cube is created
    Shipment(double len, double m, double c) {
        super(len, m);
        cost = c;
    }
}
```

```java
class DemoShipment {
    public static void main(String args[]) {
        Shipment shipment1 =
            new Shipment(10, 20, 15, 10, 3.41);
        Shipment shipment2 = new Shipment(2, 3, 4, 0.76, 1.28);
        double vol;
        vol = shipment1.volume();
        System.out.println("Volume of shipment1 is " + vol);
        System.out.println("Weight of shipment1 is " +
            shipment1.weight);
        System.out.println("Shipping cost: $" + shipment1.cost);
        System.out.println();
        vol = shipment2.volume();
        System.out.println("Volume of shipment2 is " + vol);
        System.out.println("Weight of shipment2 is " +
            shipment2.weight);
        System.out.println("Shipping cost: $" + shipment2.cost);
    }
}
```

## Ans:

Volume of shipment1 is 3000.0  
Weight of shipment1 is 10.0  
Shipping cost: $3.41  
Volume of shipment2 is 24.0  
Weight of shipment2 is 0.76  
Shipping cost: $1.28

## 8.4 何时调用构造函数

- 在类层次结构中，构造函数以派生的次序调用，从超类到子类。
- 尽管 super() 必须是子类构造函数的第一个执行语句，无论你用到了 super() 没有，这个次序不变。
- 如果 super() 没有被用到，每个超类的默认的或无参数的构造函数将执行。

## Ans:

Inside A's constructor  
Inside B's constructor  
Inside C's constructor

## 8.5 方法重写

- 子类方法与它超类方法有相同的方法名和类型声明，称方法重写（override）。
- 从子类中调用重写方法时，它总是引用子类定义的方法。而超类中定义的方法将被隐藏。

### 例 P146

### 重写（override）

```java
// Method overriding.
class A {
    int i, j;
    A(int a, int b) {
        i = a;
        j = b;
    }
    // display i and j
    void show() {
        System.out.println("i and j: " + i + " " + j);
    }
}
```

```java
class B extends A {
    int k;
    B(int a, int b, int c) {
        super(a, b);
        k = c;
    }
    // display k – this overrides show() in A
    void show() {
        System.out.println("k: " + k);
    }
}
class Override {
    public static void main(String args[]) {
        B subOb = new B(1, 2, 3);
        subOb.show();       // this calls show() in B
    }
}
```

Ans:

k: 3

![](img/489adce8323ca3a7b0e9fe701e6e665c_377_0.png)


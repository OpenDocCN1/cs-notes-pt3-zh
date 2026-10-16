
## Example 2: E-bike parts store

Task: we need to write a management system for the clerks to use in store?

- To compute the price total
- To check information for e-bikes
- Etc.

怎样设计我们的程序呢？

Solution 1: Just write a client class with a main method to call the getPrice() method in each of the concrete classes to get the prices and then add them up.

Design 1: write a class with a main method, to call the getPrice() method in the concerned classes and then add them up.

![](img/95717dc23f76db2057b9aa0c49790307_1076_0.png)

Solution 2: Design using the visitor pattern

Reason: Because the types of the parts don’t change often, and the prices of the parts will change very often.

### 设计要点：

- Need a visitor class
- Need to add an “accept” method for each classes in the class hierarchy

1) Structure: With the Visitor pattern, you define two class hierarchies:

- **Element class hierarchy- EBike**
  The class to be visited, and
- **Visitor class hierarchy- Visitor**
  define operations on the elements

2) Need an abstract parent class Visitor for
   all visitors of an abstract syntax tree.

3) Visitor must declare an operation for each
   node class.

## Design 2. using the visitor design pattern

![](img/95717dc23f76db2057b9aa0c49790307_1080_0.png)

获得某个配件的价格

获得某个配件的信息

![](img/95717dc23f76db2057b9aa0c49790307_1081_0.png)

Visitor for getting price for each piece of part, calculating total price, and getting information of each piece of part

```
Visitor pv = new PriceVisitor();
EBike bikePart = new Battery();
bikePart.accept(pv);
```

![](img/95717dc23f76db2057b9aa0c49790307_1082_0.png)

![](img/95717dc23f76db2057b9aa0c49790307_1082_1.png)

![](img/95717dc23f76db2057b9aa0c49790307_1082_2.png)

bikePart.accept(pv)

pv.visitBattery(bikePart);

bikePart.getPrice()

Interactions in the design

37

### Example 2: E-bike parts store-code

```java
public class EBikeGUI extends JFrame
implements ItemListener{
//图形界面生成代码（省略），下面是监听器代码
class ButtonActionListener implements ActionListener{
public void actionPerformed(ActionEvent e) {
Visitor pv = new PriceVisitor();
EBike bikePartObj;
if (customer select Battery) {
bikePartObj = new Battery();
}
bikePartObj.accept(pv);
}
}
}
```

```java
abstract class EBike{
    public abstract void accept(Visitor vis);
    public abstract double getPrice();
    public abstract String getDescription();
}
```

```java
public class Motor extends EBike {
    public double getPrice(){
        return 430.00;
    }
    public String getDescription(){
        return "Super Motor...";
    }
    public void accept(Visitor v) {
        System.out.println("Motor has been visited.");
        v.visitMotor(this);
    }
}
```

```java
public class Throttle extends EBike {
    public double getPrice(){
        return 155.00;
    }
    public String getDescription(){
        return "Super Throttle...";
    }
    public void accept(Visitor v) {
        System.out.println("Throttle has been visited.");
        v.visitThrottle(this);
    }
}
```

```java
public class WholeBike extends Composite {
    public WholeBike() {
        super.add(new Battery());
        super.add(new BatteryBag());
        super.add(new BatteryCable());
        super.add(new BatteryChanger());
        super.add(new BrakeHandle());
        super.add(new Controller());
        super.add(new Motor());
        super.add(new Throttle());
        super.add(new Wheel());
    }
    public void accept(Visitor v) {
        System.out.println("WholeBike has been visited.");
        super.accept(v);
    }
}
```

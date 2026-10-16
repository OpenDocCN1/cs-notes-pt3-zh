# Characteristics of Abstract Classes

+   1) use an abstract class by claiming a variable of the abstract class type and create objects of its subclasses and then call the methods in the subclasses

```
USCar myCar;
//...
if(condition1==true)
    myCar = new Lincoln();
else if(condition2==true)
    myCar = new Buik();

myCar.getInstructions()
```
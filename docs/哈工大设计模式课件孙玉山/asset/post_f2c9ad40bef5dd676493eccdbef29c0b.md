
## 3. Observer Pattern

通知观察者的两种策略：

- 1. **The push model(将观察者所需数据全部推给观察者，例如， update(Object a))**: The subject **should send the state information** that the observers may be interested in
- 2. **The pull model(主题提供接口，供观察者访问，例如update(Observable obs))**: The subject should provide an interface that enables observers to query the subject for the required state information to update their state.
- • 【注】观察者模式有许多变形

## 3. Observer Pattern

### Advantages of the Observer pattern:

- 1. 可以动态添加观察者而不需要影响主题。
  Different observers can be added dynamically without requiring any changes to the Subject class.
- 2. 当主题的状态或者逻辑发生变化的时候，观察者不受影响。
  When the state or logic of the subject changes, observers remain unaffected

## 3. Observer Pattern

- Java语言环境对观察者模式的支持。
- Java API支持Observable/Observer策略(例如: J2SDK1.4). Java提供了以下的

被观察者类

观察者接口

## 3. Observer Pattern

Java支持的观察者模式类图-既拉又推

```
Observable S = new Subject();
Observer O = new Observer1();
S.addObserver(O);
```

# Client

# Observable

+addObserver(observer:Observer)
+setChanged()
+notifyObservers(event: Object)

# Subject

O (观察者对象)

getState()

# <<interface>>
Observer

+update(o: Observable, e: Object)

# Observer1

S(主题对象), event (事件对象)

+update(o: Observable, e: Object)

利用S调用

S
event

# Java支持的观察者模式-典型交互

## Design examples using the observer design pattern

## 4. Observable/Observer example

• Example: 温度转换程序设计的例子。 We try to display temperature measures in Celsius, Fahrenheit and Kelvin.

• We use a GUI TemperatureGUI for users to enter degrees of temperature in

- – Celsius or
- – Fahrenheit or
- – Kelvin.

• Then the other 3 graphical guis will display the temperature both in Celsius and Fahrenheit.

## 4. Observable/Observer example

- - In such case, we can use observer design pattern
  - Encapsulate the TemperatureGUI as a class that implements interface Observable, and
  - Encapsulate the CelsiusGUI, FahrenheitGUI and KelvinGUI as 3 classes that implement interface Observer

## Design 1

User defined Observable/Observer pattern

## 4. Observable/Observer

- - **Design highlights**: Two interfaces
  - **Observable**
  - **Observer**
  with exactly all of their methods claimed in the design.
- - In TemperatureGUI, you need to implement all the methods:
  - **notifyObservers()**
  - **register(obs: Observer)**
  - **unRegister(obs:Observer)**

## 4. Observable/Observer

- - In the CelsiusGUI, FahrenheitGUI, and KelvinGUI, you need to implement the method
  - **update( s: Observable)**

Temperature options: Celsius

Boiler Temperature: 100

Submit

Exit

被观察者

```
public class TemperatureGUI implements Observable{
ArrayList(<Observable>) observersList = new ArrayList(<Observable>);

public void register (Observer obs) { observersList.add(obs);}
public void unRegister(Observer obs){ observersList.remove(obs); }
public void notifyObservers(String temperature) {
    for (int i = 0; i < observersList.size(); i++) {
        Observer observer=(Observer)observersList.elementAt(i);
        observer.update (this, temperature); //call update method in all the
                                            //observers
    }
}
class ButtonHandler implements ActionListener{
    public void actionPerformed(ActionEvent e){
        if (e.getActionCommand().equals(SUBMIT)){
            String tem = boilerTem.getText(); //get temperature
            setTemperature(tem); //set temperature to the private variable
            notifyObservers(bTem); //notify the observers that the temperature has
                                   //changed
        }
    }
} } }
```

```
public class CelsiusGUI extends JFrame implements Observer{
    tempGui.register(this);

    public void update( Observable subject, Object arg) {

        String t = (String) arg; // 从参数传入的温度值 the temperature value

        // parameter subject represents observable, object of TemperatureGUI is
        // passed in from here. See how to call the update method in method
        //notifyObservers in class TemperatureGUI

        TemperatureGUI tg = (TemperatureGUI)subject; //从参数传入的被观
        //察者对象
        String option = tg.getSelectedTemExpression();

        TemperatureConvertor tc = new TemperatureConvertor();
        float cTem = tc.getCelsiusTemperature(option,t);
        tempTextArea.setText(""+cTem);
    } }
```

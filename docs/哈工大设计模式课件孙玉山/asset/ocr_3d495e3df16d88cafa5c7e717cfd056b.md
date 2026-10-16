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
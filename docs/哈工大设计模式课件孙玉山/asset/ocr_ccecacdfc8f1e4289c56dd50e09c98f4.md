```
```java
public class TestObserverObservable {
    public static void main(String[] args) throws Exception {

        //create an observable object
        TemperatureGUI temperatureObj = new TemperatureGUI();

        //Create Observer objects
        CelsiusGUI cg = new CelsiusGUI();
        FahrenheitGUI fg = new FahrenheitGUI();
        KelvinGUI kg = new KelvinGUI();
    }
}
```
```

注意：这里没有addObserver方法的调用，是因为在CelsiusGUI中，已经有tempGui.register(this);
# Design Example Using the State Pattern

```
public class Yellow extends LightState{
    public Yellow(){
        state = YELLOW;
    }
    public Color setColor(){
        return Color.yellow;
    }
    public void performTask() {
        Surveillance.takePictures();
        Surveillance.doStatistics();
        changeState();
    }
    public void changeState(){
        state = RED;
        cxt.setState(state);
    }
}
```

在改变状态变量的同时，更新Context类中的状态变量
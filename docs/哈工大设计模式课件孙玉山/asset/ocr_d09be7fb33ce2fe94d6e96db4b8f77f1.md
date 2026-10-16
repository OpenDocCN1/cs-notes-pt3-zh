# Design Example Using the State Pattern

```
public class Red extends LightState{
  public Red() {
    state = RED;
  }
  public Color setColor(){
    return Color.red;
  }
  public void performTask() {
    Surveillance.takePictures();
    Surveillance.doStatistics();
    changeState();
  }
  public void changeState(){
    state = GREEN;
    cxt.setState(state);
  }
}
```

在改变状态变量的同时，更新Context类中的状态变量
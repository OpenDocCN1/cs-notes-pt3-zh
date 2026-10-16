# Facade Pattern-sample code

```
public void activate() {
    camera1.turnOn();
    camera2.turnOn();
    light1.turnOn();
    light2.turnOn();
    light3.turnOn();
    ss.activate();
    ts.activate();
    cs.activate();
    hs.activate();
    ws.activate();
    wss.activate();
    pc.activate();
    hc.activate();
    fc.activate();
    alarm.activate();
}
```

门面类在这里实现对类库的调用
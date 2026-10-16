# 解决方案二

```
abstract class Door {
    abstract void open();
    abstract void close();
}
```

```
interface Alarm {
    void alarm();
}
```

```
class AlarmDoor extends Door implements Alarm {
    void open() { ... }
    void close() { ... }
    void alarm() { ... }
}
```
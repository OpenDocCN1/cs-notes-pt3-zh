# Thread类和Runnable接口的联系

+   Thread类的定义

+   public class Thread extends Object implements Runnable

+   Thread类的部分定义

```
private Runnable target;
public Thread(Runnable target, String name) {
    init(null, target, name, 0);
}
private void init(ThreadGroup g, Runnable target, String name,long stackSize) {
    ...
    this.target = target;
    ...
}
public void run() {
    if (target != null) {
        target.run();
    }
}
```

![](bbox=[0.52, 0.49, 0.96, 0.82])
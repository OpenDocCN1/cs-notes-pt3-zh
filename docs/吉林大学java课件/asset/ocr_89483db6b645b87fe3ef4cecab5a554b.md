# 主板和CPU的例子

```
class AmdCPU implements CPU
{
    public void start(){
        System.out.println("AMD Start");
    }
    public void stop(){
        System.out.println("AMD Stop.");
    }
}
class MainBoard
{
    public void useCPU(CPU p) {
        p.start();
        p.stop();
    }
}
```

![](bbox=[0.419, 0.556, 0.593, 0.724])

> 方法useCPU只需了解接口CPU，不需要了解CPU对应的类，比如AmdCPU、IntelCPU等等
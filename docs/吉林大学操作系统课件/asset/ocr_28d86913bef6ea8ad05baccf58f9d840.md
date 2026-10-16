# 例子：生产/消费问题--Java

```
public class Bounded Buffer {
    public BoundedBuffer() {    //缓冲区变量定义
        count=0; in=0; out=0;
        buffer=new Object[BUFFER_SIZE];
    }
}
```
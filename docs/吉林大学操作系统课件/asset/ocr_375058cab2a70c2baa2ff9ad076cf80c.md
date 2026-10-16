# 读者 / 写者问题-Java solution

```
public synchronized void startRead() {
    while (dbWriting==true) {
        try {
            wait();
        }catch(InterruptedException e){}
        ++readCount;
        if (readCount==1)
            dbReading=true;
    }
```
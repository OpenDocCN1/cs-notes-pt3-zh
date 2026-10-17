```
```java
class MultiThreadDemo {
    public static void main(String args[]) {
        new NewThread("One");        // start threads
        new NewThread("Two");        // 三个子线程共享CPU
        new NewThread("Three");
        try {
            // wait for other threads to end
            Thread.sleep(10000);
            // sleep(10000) 使主线程沉睡十秒确保它最后结束
        } catch (InterruptedException e) {
            System.out.println("Main thread Interrupted");
        }
        System.out.println("Main thread exiting.");
    }
}
```
```
```
```java
// wait for threads to finish
try {
    System.out.println("Waiting for threads to finish.");
    ob1.join();
    ob2.join();
} catch (InterruptedException e) {
    System.out.println("Main thread Interrupted");
}
System.out.println("Main thread exiting.");
}
}
```
```

Ans: 同例P212
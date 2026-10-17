```
class PCFixed {
public static void main(String args[]) {
Q q = new Q();
new Producer(q);
new Consumer(q);
System.out.println("Press Control-C to stop.");
}
}
```

// get()执行，wait()被调用。这使执行挂起直到Producer 告知数据已经预备好。这时，get() 被恢复执行。

// 获取数据后，get()调用notify()。这告诉Producer可以向序列中输入更多数据。

// 在put()内，wait()挂起执行直到Consumer取走了序列中的项目。当执行再继续，下一个数据项目被放入序列，notify()被调用，这通知Consumer它应该移走该数据。
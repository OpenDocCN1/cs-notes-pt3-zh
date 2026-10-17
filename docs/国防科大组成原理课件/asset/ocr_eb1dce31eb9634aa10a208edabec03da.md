# 实现锁机制

+   - 自旋锁（Spin lock）
+     - 最基本的锁实现方式，处理器核围绕一个锁不停地旋转而请求获得该锁
+   - 自旋锁缺点：
+     - 一个处理器核获得锁后，其他处理器核循环执行Test_and_Set指令访问锁变量，试图获取锁，从而在片上互连上产生大量的访存通信
+     - 一种简单改进措施：在Test_and_Set指令之间加入一定的延迟，减少等待阶段Test_and_Set指令自旋执行的次数以减轻访存的压力

```
Void acquire_lock(){
    while (test_and_set(lock)!=0;
}
```

```
Void unlock(){
    lock=0;        //释放锁
}
```
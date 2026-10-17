# 处理器一致性

+   - 由 Goodman 提出的处理器一致性(Processor Consistency)比顺序一致性弱，处理器一致性对访存事件发生次序施加的限制：
+     - 在任一取数操作 LOAD 允许被执行之前，所有在同一处理器中先于这一 LOAD 的取数操作都已完成；
+     - 在任一存数操作 STORE 允许被执行之前，所有在同一处理器中先于这一 STORE 的访存操作(包括LOAD 和STORE)都已完成。
+   - 上述条件允许STORE 之后的LOAD 越过STORE 而执行，放松了顺序一致性模型对访存次序的限制。
+   - 实际上是把Write Buffer变得让用户可见
+     - 如：Store提交后在Write Buffer，还没有写Cache/内存，后面的Load已经从Cache取回数据，此时收到对Load访问Cache行的一个无效请求
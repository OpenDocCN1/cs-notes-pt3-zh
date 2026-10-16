# 找到哪些地方要停，什么时候再走？

需要让“进程走走停停”来保证多进程合作的合理有序

# 这就是进程同步

```
while (true) {
 while(counter== BUFFER_SIZE)
 缓存区满，生产者要停;
 buffer[in] = item;
 in = (in + 1) % BUFFER_SIZE;
 counter++;
 }
```

```
while (true) {
 while(counter== 0)
 缓存区空，消费者要停;
 item = buffer[out];
 out = (out + 1) % BUFFER_SIZE;
 counter--;
 }
```

> 发信号让消费者再走...

> 发信号让生产者再走...

![](bbox=[0.75, 0.75, 0.95, 0.95])
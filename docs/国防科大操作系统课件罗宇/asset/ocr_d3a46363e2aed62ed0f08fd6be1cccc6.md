# Receive(A):

```
begin
  P(Sm);
  P(mutex);
    从本进程的消息队列取一个buffer f;
  V(mutex);
    从buffer f中取得消息正文送A, 并得到
    sender’s pid作为Receive( )的返回
值;
    ...
    dispose(f); #释放buffer f到缓冲池
    ...
end;
```

注:new, dispose函数对缓冲池的访问也需要互斥。
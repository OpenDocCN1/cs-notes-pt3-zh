# 多进程实现前述的读写并发程序示意

（假设a，b都在两进程都可访问的共享区）

```
pid = fork ( );
if pid == 0 then
{ read (b) ;
  exit (0) ; }
else
  read (a) ;
return_pid = wait (&status) ;
c = a+b;
write (c) ;
```
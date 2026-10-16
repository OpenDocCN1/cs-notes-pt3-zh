# 继续tty_write这一核心函数

```
在linux/kernel/tty_io.c中
int tty_write(unsigned channel, char *buf, int nr)
{
...
    char c, *b=buf;
    while(nr>0 && !FULL(tty->write_q)) {
        c = get_fs_byte(b);    // fs:从用户缓存区读!
        if(c=='\r') {PUTCH(13,tty->write_q);continue;}
        if(O_LCUC(tty)) c = toupper(c);
        b++; nr--;  PUTCH(c,tty->write_q);
    } //输出完事或写队列满！
    tty->write(tty);
}
```

tty->write应该就是真的开始输出屏幕了！
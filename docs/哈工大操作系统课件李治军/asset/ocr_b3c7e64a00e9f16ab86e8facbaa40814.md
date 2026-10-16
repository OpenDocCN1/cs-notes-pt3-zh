# 系统调用(write)

read_write.c

# 字符设备接口(crw_table[])

char_dev.c

tty设备写(tty_write)

tty设备读(tty_read)

secondary

tty_io.c

write_q队列

read_q队列

回显

console.c

显示器写(con_write)

keyboard.S

显示器

主机键盘

问题：如果按下F12让ls的输出为*，怎么办？如果只让回显为*，怎么办？如果是让输出的文件为*，又怎么办？

![](bbox=[0.86, 0.1, 0.97, 0.38])

![](bbox=[0.92, 0.81, 0.99, 0.94])
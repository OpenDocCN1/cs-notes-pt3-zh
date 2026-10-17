# 10.6.1 三者共有的特性

IPC资源 表示单独的消息队列、共享内存或是信号量集合

# 三者均有XXXget（）及XXXctl（）函数

（XXX代表msg、sem、shm三者之一）

# （a） XXXget（）函数

两个共同参数：key和oflag。

key既可由ftok（）函数产生，也可以是IPC_PRIVATE常量，key值是IPC资源的外 部表示。
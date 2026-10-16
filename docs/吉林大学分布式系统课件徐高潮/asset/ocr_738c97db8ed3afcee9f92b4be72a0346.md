# 第二章 进程通信

# 2.1 同一节点上的进程间通信

+   ◆ 消息队列

队列中的消息能够以随意的顺序进行检索，因为可以通过消息的类型把消息从队列中检索出来。

+   ➢ 创建和打开一个消息队列：

```
int open_queue(key_t key)
{
    int qid;
    if((qid=msgget(key,IPC_CREAT|0660))==-1)
    {
        return(-1);
    }
    return(qid);
}
```
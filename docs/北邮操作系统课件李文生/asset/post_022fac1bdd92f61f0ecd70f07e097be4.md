
## Indirect Communication(2/3)

+   **Mailbox sharing**
+   - P₁, P₂, and P₃ share mailbox A.
+   - P₁ sends; P₂ and P₃ receive.
+   - Who gets the message?

+   **Solutions**
+   - Allow a link to be associated with at most two processes.
+   - Allow only one process at a time to execute a receive operation.
+   - Allow the system to select arbitrarily the receiver. Sender is notified who the receiver was.

## Indirect Communication(3/3)

+   - **If the mailbox is owned by a process**
+     - owner can only receive messages through this mailbox
+     - user can only send messages to the mailbox
+   - **if the mailbox is owned by the operating system**
+     - the mailbox is independent
+     - not attached to any particular process
+   - **OS provides mechanism allowing a process to do following operations**
+     - create a new mailbox
+     - send and receive messages through mailbox
+     - delete a mailbox

## Buffering

Queue of messages attached to the link; implemented in one of three ways.

+   - **Zero capacity** – 0 messages  
     Sender must wait for receiver (rendezvous).  
+   - **Bounded capacity** – finite length of *n* messages  
     Sender must wait if link full.  
+   - **Unbounded capacity** – infinite length  
     Sender never waits.

## Supplement: pipeline(管道)

+   - 管道是一条在进程间以字节流方式传送数据的通信通道。
+   - 由OS核心的缓冲区（通常几十KB）来实现，是单向的；
+   - 常用于命令行所指定的输入输出重定向和管道命令。
+   - 使用前要建立相应的管道，然后才可使用。
+   - 管道逻辑上可以看作管道文件，物理上则是由文件系统的高
     速缓存区构成。
+   - 管道分为有名管道和无名管道
+   - 管道按先进先出（FIFO）的方式传送消息，且只能单向传
     送消息。
+   - 管道操作
     - 发送进程利用文件系统的系统调用 write（fd[1], buf, size）
       把buf中长度为size字符的消息送入管道入口fd[1];
     - 接收进程利用文件系统的系统调用 read（fd[0], buf, size）
       从管道出口fd[0]读出size字符的消息放入buf中。

## Supplement: 管道应用示例

```
```c
#include<stdio.h>
main()
{
  int pid,fd[2];
  char buf[30],s[30];
  pipe(fd);
  while((pid=fork())==-1);
  if (pid==0) {
    sprintf(buf, "this is an example\n");
    write(fd[1],buf,30);
    exit(0);
  }
  else {
    wait(0);
    read(fd[0],s,30);
    printf("%s",s);
  }
}
```
```

## 3.5 example of IPC systems

## C program illustrating POSIX shared-memory API

```
#include <stdio.h>
#include <sys/shm.h>
#include <sys/stat.h>
int main()
{
    int segment_id;                 // the id for the shared memory segment
    char* shared_memory;            // a pointer to the shared memory segment
    const int segment_size = 4096; // the size of the shared memory segment

    /** allocate a shared memory segment */
    segment_id = shmget (IPC_PRIVATE, segment_size, S_IRUSR | S_IWUSR);

    /** attach the shared memory segment */
    shared_memory = (char *) shmat (segment_id, NULL, 0);

    printf("shared memory segment %d attached at address %p\n", segment_id, shared_memory);
}
```

```
/** write a message to the shared memory segment */
sprintf(shared_memory, "Hi there!");

// now print out the string from shared memory
printf("*%s*\n", shared_memory);

/** now detach the shared memory segment */
if ( shmdt(shared_memory) == -1)
{
    fprintf(stderr, "Unable to detach\n");
}

/** now remove the shared memory segment */
shmctl(segment_id, IPC_RMID, NULL);

return 0;
}
```

## message passing facility in Windows XP-- LPC

+   - LPC Communicates between two processes on the same machine.
+   - a port object is used to establish and maintain a connection between two processes.
+   - two types of ports:
+     - Connection ports
       named objects, visible to all processes;
       used to set up communication channels.
+     - Communication ports
+   - Communication works
+     - Client opens a handle to the subsystem’s connection port object
+     - Client sends a connection request
+     - Server creates two private communication ports and returns the handle to one of them to the client
+     - Client and server use the corresponding port handle to send messages or callbacks and to listen for replies

## Two types of message-passing techniques

+   - Used for small messages (up to 256 bytes)
     simplest.
     uses the port’s message queue as intermediate storage and copies the message from one process to the other.
+   - A section object (for large messages)
     sets up a region of shared memory.
     A small message is sent that contains a pointer and size information about the section object.

## callback mechanism

+   - Can be used when either the client or the server cannot respond immediately to a request.
+   - Allows to perform asynchronous message handling.

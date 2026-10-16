

## 进程创建 (3/3)

- **地址空间**
  - 子进程是父进程的副本。
  - 子进程中加载了程序。

- **UNIX 示例**
  - 每个进程都由其进程标识符标识，这是一个唯一的整数
  - 系统调用 **fork** 创建新进程
  - 系统调用 **exec** 在 fork 之后使用，用来用新程序替换子进程的内存空间。

## 用于 fork 分离进程的 C 程序

```
#include <sys/types.h>
#include <stdio.h>
#include <unistd.h>
void main()
{
pid_t pid;
pid=fork();  // fork another process
if (pid<0) {  // error occurred
fprintf(stderr, "Fork failed");
exit(-1);
}
else if (pid==0) {  // child process
execlp("/bin/ls", "ls", NULL);
} else {  // parent process
wait(NULL);  /* parent process will wait for the child to complete */
printf("Child Complete");
exit(0);
}
}
```

## 进程创建

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_208_0.png)

## 使用 win32 API 创建一个单独的进程

```c
#include <windows.h>
#include <stdio.h>
int main( VOID )
{
    STARTUPINFO si;
    PROCESS_INFORMATION pi;
    ZeroMemory( &si, sizeof(si) ); // allocate memory
    si.cb = sizeof(si);
    ZeroMemory( &pi, sizeof(pi) );
```
```

```c
// Start the child process.
if( !CreateProcess( NULL,  // No module name (use command line).
    "C:\\WINDOWS\\system32\\mspaint.exe",        // Command line.
    NULL,        // Process handle not inheritable.
    NULL,        // Thread handle not inheritable.
    FALSE,       // Set handle inheritance to FALSE.
    0,           // No creation flags.
    NULL,        // Use parent's environment block.
    NULL,        // Use parent's starting directory.
    &si,         // Pointer to STARTUPINFO structure.
    &pi )        // Pointer to PROCESS_INFORMATION structure.
{
    printf( "CreateProcess failed (%d).\n", GetLastError() );
    return -1;
}

// Wait until child process exits.
WaitForSingleObject( pi.hProcess, INFINITE );
printf( "parent exit" );
// Close process and thread handles.
CloseHandle( pi.hProcess );
CloseHandle( pi.hThread );
```
```

## 进程终止

- 批处理作业发出 *Halt* 指令
- 用户注销
- 退出一个应用程序
- 错误和故障条件

## 补充：
### 进程终止原因 (1/2)

- 正常完成
- 超时
- 内存不可用
- 边界违规
- 保护错误
  - 示例 写入只读文件
- 算术错误
- 时间超限
  - 进程等待某个事件的时间超过了指定的最大值

## 补充：
### 进程终止原因 (2/2)

- I/O 失败（例如 文件未找到）

- 无效指令
  - 当尝试执行数据时发生

- 特权指令

- 数据误用（例如 类型错误）

- 操作系统干预
  - 例如 当发生死锁时

- 父进程终止因此子进程终止

- 父进程请求

## 进程终止

- 进程执行最后一条语句并请求操作系统删除它（通过 `exit`）。
  - 从子进程向父进程输出数据（通过 `wait`）。
  - 进程的资源由操作系统释放。

- 父进程可能因多种原因终止其子进程的执行（通过 `abort`）：
  - 子进程超出了其已分配资源的使用量。
  - 分配给子进程的任务不再需要。
  - 父进程正在退出。
    - 如果其父进程终止，操作系统不允许子进程继续。
    - 级联终止，通常由操作系统发起。

## 3.4 进程间通信

- **_独立_** 进程不能影响也不能被其他进程的执行所影响。
- **_协作_** 进程可以影响或被其他进程的执行所影响
- 进程协作的优点
  - 信息共享
  - 计算加速
  - 模块化
  - 便利性
- 两种基本模型
  - 共享内存
  - 消息传递


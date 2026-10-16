# execve 示例

+   在子进程中用当前的环境执行 “/bin/ls -lt /usr/include”

(argc == 3)
myargv
myargv[argc] = NULL
myargv[2]
myargv[1]
myargv[0]
"/usr/include"
"-lt"
"/bin/ls"
environ
envp[n] = NULL
envp[n-1]
...
envp[0]
"PWD=/usr/droh"
"USER=droh"

```
if ((pid = Fork()) == 0) { /* Child runs program */
    if (execve(myargv[0], myargv, environ) < 0) {
        printf("%s: Command not found.\n", myargv[0]);
        exit(1);
    }
}
```
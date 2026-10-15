# Call from Kernel to User

+   - UNIX Signal
+     - Register signal handler
+     - Kernel checks signal before iret
+     - Kernel calls handler if a signal is pending
+       - How?

```
void foo(int signo) {
    printf("You wanna kill me?\n");
    return;
}

int main() {
    signal(SIGINT, foo);
    while (1) {
        printf("I'm still alive\n");
        sleep (1)
    }
}
```
# System Call Example

```
First, call write(1, "hello, world\n", 13)

9    movl $4, %eax        System call number 4
10   movl $1, %ebx        stdout has descriptor 1
11   movl $string, %ecx  Hello world string
12   movl $len, %edx     String length
13   int  $0x80          System call code

Next, call exit(0)

14   movl $1, %eax        System call number 0
15   movl $0, %ebx        Argument is 0
16   int  $0x80           System call code
```


## swap_add 中的主体代码

```
9 movl %eax, (%edx)
    Store y at *xp
```

```
10 movl %ebx, (%ecx)
    Store x at *yp
```

调用者的栈帧

|  |  |
|---|---|
| 24 | 保存的 %ebp |
| 20 | arg2(534) |
| 16 | arg1(1057) |
| 12 | yp(&arg2) |
| 8 | xp(&arg1) |
| 4 | 返回地址 |
| 0 | 保存的 %ebp |
| -4 | 保存的 %ebx |

%edx xp(= &arg1 = %ebp + 16)

%ecx yp(= &arg2 = %ebp + 20)

%ebx 534

%eax 1057

swap_add 的栈帧

## swap_add 中的结束代码

```
12 popl %ebx    Restore %ebx
```

调用者的栈帧

|  |  |
|---|---|
| 24 | 保存的 %ebp |
| 20 | arg2(534) |
| 16 | arg1(1057) |
| 12 | yp(&arg2) |
| 8 | xp(&arg1) |
| 4 | 返回地址 |
| 0 | 保存的 %ebp |
| -4 | 保存的 %ebx |

%ebp
%esp

swap_add 的栈帧

%edx xp(= &arg1 = %ebp + 16)

%ecx yp(= &arg2 = %ebp + 20)

%ebx 原始值

%eax 1591

## swap_add 中的结束代码

```
12 popl %ebx    Restore %ebx
13 movl %ebp, %esp    Restore %esp
```

调用者的栈帧

|  |  |
|---|---|
| 24 | 保存的 %ebp |
| 20 | arg2(534) |
| 16 | arg1(1057) |
| 12 | yp(&arg2) |
| 8 | xp(&arg1) |
| 4 | 返回地址 |
| 0 | 保存的 %ebp |
| -4 | 保存的 %ebx |

%edx xp(= &arg1 = %ebp + 16)

%ecx yp(= &arg2 = %ebp + 20)

%ebx 原始值

%eax 1591

swap_add 的栈帧

![](img/b3f8b91675c485f1e811aa092ebbf3d4_511_0.png)

## swap_add 中的结束代码

```
12 popl %ebx    Restore %ebx
13 movl %ebp, %esp
    Restore %esp
14 popl %ebp    Restore %ebp
```

调用者的栈帧

|  |  |
|---|---|
| 0 | 保存的 %ebp |
| -4 | arg2(534) |
| -8 | arg1(1057) |
| -12 | yp(&arg2) |
| -16 | xp(&arg1) |
| -20 | 返回地址 |
|  | 保存的 %ebp |
|  | 保存的 %ebx |

%ebp

%esp

%edx xp(= &arg1 = %ebp + 16)

%ecx yp(= &arg2 = %ebp + 20)

%ebx 原始值

%eax 1591

## swap_add 中的结束代码

```
12 popl %ebx    Restore %ebx
13 movl %ebp, %esp
    Restore %esp
14 popl %ebp    Restore %ebp
15 ret          Return to caller
```

- 按值调用

%edx xp(= &arg1 = %ebp + 16)
%ec x yp(= &arg2 = %ebp + 20)
%ebx 原始值
%eax 1591

调用者的栈帧

|  |  |
|---|---|
| 0 | 保存的 %ebp |
| -4 | arg2(534) |
| -8 | arg1(1057) |
| -12 | yp(&arg2) |
| -16 | xp(&arg1) |
| -20 | 返回地址 |
|  | 保存的 %ebp |
|  | 保存的 %ebx |

%ebp

%esp

## 递归示例

```
1 int fib_rec(int n)
2 {
3     int prev_val, val;
4
5     if (n <= 2)
6         return 1;
7     prev_val = fib_rec(n-2);
8     val = fib_rec(n-1);
9     return prev_val + val;
10 }
```

## 设置代码

```asm
fib_rec:
pushl %ebp
movl %esp,%ebp
subl $16,%esp
pushl %esi
pushl %ebx
```

保存旧的 %ebp  
将 %ebp 设置为 *帧指针*  
在栈上分配 16 字节  
保存 %esi（偏移 -20）  
保存 %ebx（偏移 -24）

## 递归

![](img/b3f8b91675c485f1e811aa092ebbf3d4_516_0.png)

## 主体代码

|  | 代码 | 注释 |
|---|---|---|
| 7 | movl 8(%ebp),%ebx | 获取 n |
| 8 | cmpl $2,%ebx | 比较 n:2 |
| 9 | jle .L24 | 如果 <=，则跳转到终止 |
| 10 | addl $-12,%esp | 在栈上分配 12 字节 |
| 11 | leal -2(%ebx),%eax | 计算 n-2 |
| 12 | pushl %eax | 压栈作为参数 |
| 13 | call fib_rec | 调用 fib_rec(n-2) |

## 递归

栈帧

![](img/b3f8b91675c485f1e811aa092ebbf3d4_518_0.png)

## 主体代码

```
14 movl %eax,%esi
Store result in %esi
```

```
15 addl $-12,%esp
Allocate 12 bytes to stack
```

```
16 leal -1(%ebx),%eax
Compute n-1
```

```
17 pushl %eax
Push as argument
```

```
18 call fib_rec
Call fib_rec(n-1)
```

```
19 addl %esi,%eax
Compute val+nval
```

```
20 jmp .L25
Go to done
```

![](img/b3f8b91675c485f1e811aa092ebbf3d4_520_0.png)

## 终止条件

```
21 .L24:
22     movl $1,%eax

terminate:
Return value 1
```

## 结束代码

```
23 .L25: done:
24     leal -24(%ebp),%esp    Set stack to offset -24
25     popl %ebx             Restore %ebx
26     popl %esi             Restore %esi
27     movl %ebp,%esp         Restore stack pointer
28     popl %ebp             Restore %ebp
29     ret                  Return
```

## 排列

```
#include <stdio.h>

void permute(int a[], int n, int k)
{
    int i;
    if (k == 0) {
        for ( i=0; i<n; i++)
            printf("%d", a[i]);
        printf("\n");
    }
}
```


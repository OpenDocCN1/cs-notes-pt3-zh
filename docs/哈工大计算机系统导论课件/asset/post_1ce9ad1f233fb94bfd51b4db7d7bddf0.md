
## x86-64 Linux的寄存器用法#1

- **%rax**
  - 返回值
  - 调用者保存
  - 被调用过程可修改
- **%rdi, ..., %r9**
  - 传递函数参数
  - 调用者保存
  - 被调用过程可修改
- **%r10, %r11**
  - 调用者保存
  - 被调用过程可修改

返回值

参数

调用者保存的临时值

![](img/7ab811dea080313a753fa0ae68528fa9_591_0.png)

## x86-64 Linux的寄存器用法#2

- %rbx, %r12, %r13, %r14
  - 被调用者保存并恢复
- %rbp
  - 被调用者保存并恢复
  - 可用作栈帧指针
- %rsp
  - 被调用者保存的特殊形式
  - 在离开过程时，恢复为原始值 (CALL之前的值)

![](img/7ab811dea080313a753fa0ae68528fa9_592_0.png)

## 被调用者保存——实例#1

```c
long call_incr2(long x) {
    long v1 = 15213;
    long v2 = incr(&v1, 3000);
    return x+v2;
}
```

```asm
call_incr2:
    pushq   %rbx
    subq    $16, %rsp
    movq    %rdi, %rbx
    movq    $15213, 8(%rsp)
    movl    $3000, %esi
    leaq    8(%rsp), %rdi
    call    incr
    addq    %rbx, %rax
    addq    $16, %rsp
    popq    %rbx
    ret
```

### 初始化栈结构

![](img/7ab811dea080313a753fa0ae68528fa9_593_0.png)

### 结果栈结构

![](img/7ab811dea080313a753fa0ae68528fa9_593_1.png)

## 被调用者保存——实例#2

```
long call_incr2(long x) {
	long v1 = 15213;
	long v2 = incr(&v1, 3000);
	return x+v2;
}
```

```
call_incr2:
	pushq %rbx
	subq $16, %rsp
	movq %rdi, %rbx
	movq $15213, 8(%rsp)
	movl $3000, %esi
	leaq 8(%rsp), %rdi
	call incr
	addq %rbx, %rax
	addq $16, %rsp
	popq %rbx
	ret
```

![](img/7ab811dea080313a753fa0ae68528fa9_594_0.png)

![](img/7ab811dea080313a753fa0ae68528fa9_594_1.png)

## # 主要内容

- 过程
  - 栈结构
  - 调用约定
    - 传递控制
    - 传递数据
    - 管理局部数据
  - 递归

## 递归函数

```
/* Recursive popcount */
long pcount_r(unsigned long x) {
    if (x == 0)
        return 0;
    else
        return (x & 1) + pcount_r(x >> 1);
}
```

```
pcount_r:
    movl    $0, %eax
    testq   %rdi, %rdi
    je      .L6
    pushq   %rbx
    movq    %rdi, %rbx
    andl    $1, %ebx
    shrq    %rdi # (by 1)
    call    pcount_r
    addq    %rbx, %rax
    popq    %rbx
.L6:
    rep; ret
```

## 递归函数的终止条件

```
/* Recursive popcount */
long pcount_r(unsigned long x) {
    if (x == 0)
        return 0;
    else
        return (x & 1) + pcount_r(x >> 1);
}
```

```
pcount_r:
    movl $0, %eax
    testq %rdi, %rdi
    je .L6
    pushq %rbx
    movq %rdi, %rbx
    andl $1, %ebx
    shrq %rdi #(by 1)
    call pcount_r
    addq %rbx, %rax
    popq %rbx
.L6:
    rep; ret
```

| 寄存器 | 用途 | 类型 |
| --- | --- | --- |
| %rdi | x | 参数 |
| %rax | 返回值 | 返回值 |

## 递归函数的寄存器保存

```
/* Recursive pcount */
long pcount_r(unsigned long x) {
  if (x == 0)
    return 0;
  else
    return (x & 1) + pcount_r(x >> 1);
}
```

| 寄存器 | 用途 | 类型 |
|---|---|---|
| %rdi | x | 参数 |

![](img/7ab811dea080313a753fa0ae68528fa9_598_0.png)

```
pcount_r:
  movl   $0, %eax
  testq  %rdi, %rdi
  je     .L6
  pushq  %rbx
  movq   %rdi, %rbx
  andl   $1, %ebx
  shrq   %rdi # (by 1)
  call   pcount_r
  addq   %rbx, %rax
  popq   %rbx
.L6:
  rep; ret
```

## 递归函数的调用创建

```
/* Recursive popcount */
long pcount_r(unsigned long x) {
    if (x == 0)
        return 0;
    else
        return (x & 1) + pcount_r(x >> 1);
}
```

```
pcount_r:
    movl    $0, %eax
    testq   %rdi, %rdi
    je      .L6
    pushq   %rbx
    movq    %rdi, %rbx
    andl    $1, %ebx
    shrq    %rdi # (by 1)
    call    pcount_r
    addq    %rbx, %rax
    popq    %rbx
.L6:
    rep; ret
```

| 寄存器 | 用途 | 类型 |
|---|---|---|
| %rdi | x >> 1 | Rec. 参数 |
| %rbx | x & 1 | Callee-saved |

## 递归函数调用

```
/* Recursive popcount */
long pcount_r(unsigned long x) {
    if (x == 0)
        return 0;
    else
        return (x & 1) + pcount_r(x >> 1);
}
```

| 寄存器 | 用途 | 类型 |
|---|---|---|
| %rbx | x & 1 | 被调用者保存 |
| %rax | 递归调用的返回值 |  |

```
pcount_r:
    movl    $0, %eax
    testq   %rdi, %rdi
    je      .L6
    pushq   %rbx
    movq    %rdi, %rbx
    andl    $1, %ebx
    shrq    %rdi # (by 1)
    call    pcount_r
    addq    %rbx, %rax
    popq    %rbx
.L6:
    rep; ret
```

## 递归函数的完成

```
/* Recursive popcount */
long pcount_r(unsigned long x) {
    if (x == 0)
        return 0;
    else
        return (x & 1) + pcount_r(x >> 1);
}
```

| 寄存器 | 用途 | 类型 |
| --- | --- | --- |
| %rax | 返回值 | 返回值 |

```
pcount_r:
    movl    $0, %eax
    testq   %rdi, %rdi
    je      .L6
    pushq   %rbx
    movq    %rdi, %rbx
    andl    $1, %ebx
    shrq    %rdi # (by 1)
    call    pcount_r
    addq    %rbx, %rax
    popq    %rbx
.L6:
    rep; ret
```

![](img/7ab811dea080313a753fa0ae68528fa9_602_0.png)



## 优化限制因素

- 寄存器溢出
  - 仅有 6 个寄存器可用（IA32）
  - 使用栈（内存）作为存储

| Machine | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---:|---:|---:|---:|---:|
| IA32 | 2.12 | 1.76 | 1.45 | 1.39 | 1.90 | 1.99 |
| X86-64 | 2.00 | 1.50 | 1.00 | 1.00 | 1.01 | 1.00 |

## 示例

```
IA32 code. Unroll x5, accumulate x5
data_t = int, OP = +, i in %edx, data in %eax, limit at %ebp-20
```

```asm
.L291:
    imull  (%eax,%edx,4), %ecx
    movl   -16(%ebp), %ebx
    imull  4(%eax,%edx,4), %ebx
    movl   %ebx, -16(%ebp)
    imull  8(%eax,%edx,4), %edi
    imull  12(%eax,%edx,4), %esi
    movl   -28(%ebp), %ebx
    imull  16(%eax,%edx,4), %ebx
    movl   %ebx, -28(%ebp)
    addl   $5, %edx
    cmpl   %edx, -20(%ebp)
    jg     loop

loop:
    x0 = x0 * data[i]
    Get x1
    x1 = x1 * data[i+1]
    Store x1
    x2 = x2 * data[i+2]
    x3 = x3 * data[i+3]
    Get x4
    x4 = x4 * data[i+4]
    Store x4
    i += 5
    Compare limit:i
    If >, goto loop
```

## 优化限制因素

- 寄存器溢出
  - 仅有 6 个寄存器可用（IA32）
  - 使用栈（内存）作为存储
- 分支预测
  - 推测执行
  - 误预测惩罚

## 分支预测

- 挑战
  - 指令控制单元必须领先执行单元很多
  - 以生成足够的运算来保持 EU 忙碌
- 推测执行
  - 猜测分支会走向何方
  - 开始在预测位置执行指令
    - 但不要实际修改寄存器或内存数据

## 示例：循环

```
80488b1: movl (%ecx,%edx,4),%eax
80488b4: addl %eax,(%edi)
80488b6: incl %edx
80488b7: cmpl %esi,%edx
80488b9: jl 80488b1
80488be: movl (%ecx,%edx,4),%eax
```

分支未 taken

分支 taken

```
80488b1: movl (%ecx,%edx,4),%eax
80488b4: addl %eax,(%edi)
80488b6: incl %edx
80488b7: cmpl %esi,%edx
80488b9: jl 80488b1
```

## 循环中的分支预测

```
80488b1:    movl    (%ecx,%edx,4),%eax
80488b4:    addl    %eax, (%edi)
80488b6:    incl    %edx
80488b7:    cmpl    %esi,%edx
80488b9:    jl      80488b1
```

```
80488b1:    movl    (%ecx,%edx,4),%eax
80488b4:    addl    %eax, (%edi)
80488b6:    incl    %edx
80488b7:    cmpl    %esi,%edx
80488b9:    jl      80488b1
```

```
80488b1:    movl    (%ecx,%edx,4),%eax
80488b4:    addl    %eax, (%edi)
80488b6:    incl    %edx
80488b7:    cmpl    %esi,%edx
80488b9:    jl      80488b1
```

```
80488b1:    movl    (%ecx,%edx,4),%eax
80488b4:    addl    %eax, (%edi)
80488b6:    incl    %edx
80488b7:    cmpl    %esi,%edx
80488b9:    jl      80488b1
```

假设向量长度 = 100

i = 98

预测 Taken（正确）

i = 99

预测 Taken（糟糕）

读取无效位置

i = 100

i = 101

已执行

已获取

## 分支误预测失效

```asm
80488b1:    movl    (%ecx,%edx,4),%eax
80488b4:    addl    %eax,(%edi)
80488b6:    incl    %edx
80488b7:    cmpl    %esi,%edx
80488b9:    jl      80488b1

80488b1:    movl    (%ecx,%edx,4),%eax
80488b4:    addl    %eax,(%edi)
80488b6:    incl    %edx
80488b7:    cmpl    %esi,%edx
80488b9:    jl      80488b1
80488be:    movl    (%ecx,%edx,4),%eax
```

假设向量长度 = 100

i = 98

> 预测 Taken（正确）

i = 99

> 绝对不会 taken

## 分支误预测恢复

- 性能开销
  - Core i7 上误预测浪费约 ~44 个时钟周期
  - 不必过度担心可预测的分支
  - 例如，闭合循环的分支通常会被预测为 taken，并且仅在最后一次循环时才会产生误预测惩罚

## 编写合适的代码

```c
void minmax1(int a[],
             int b[], int n)
{
    int i;
    for (i = 0; i < n; i++) {
        if (a[i] > b[i]) {
            int t = a[i];
            a[i] = b[i];
            b[i] = t;
        }
    }
}
```

```c
void minmax2(int a[],
             int b[], int n)
{
    int i;
    for (i = 0; i < n; i++) {
        int min = a[i] < b[i] ? a[i] : b[i];
        int max = a[i] < b[i] ? b[i] : a[i];
        a[i] = min;
        b[i] = max;
    }
}
```

| Function | random | predictable |
|---|---|---:|---:|
| minmax1 | 14.5 | 3.0–4.0 |
| minmax2 | 5.0 | 5.0 |




## 循环展开

```
void combine5(vec_ptr v, int *dest)
{
    int i;
    int length = vec_length(v);
    int limit = length - 2;
    int *data = get_vec_start(v);
    int x = IDENT;

    /* combine 3 elements at a time */
    for (i = 0; i < limit; i+=3)
        x = x OPER data[i] OPER data[i+1] OPER data[i+2];

    /* finish any remaining elements */
    for (; i < length; i++)
        x = x OPER data[i];

    *dest = x;
}
```

## 翻译

- 加载可以流水线，因为没有依赖关系
- 只有一组循环控制操作

```
load (%rax,%rdx.0,4) ➔ t.1a
addq t.1a, %rcx.0c ➔ %rcx.1a
load 4(%rax,%rdx.0,4) ➔ t.1b
addq t.1b, %rcx.1a ➔ %rcx.1b
load 8(%rax,%rdx.0,4) ➔ t.1c
addq t.1c, %rcx.1b ➔ %rcx.1c
addq $3,%rdx.0 ➔ %rdx.1
cmpq %rdx.1, %rbp ➔ cc.1
jg-taken cc.1
```

## 循环展开

- 提高性能
  - 减少操作次数（例如循环索引和条件分支）
  - 转换代码以减少关键路径中的操作次数
- 两种整数操作的 CPE 均有所改善
- 但两种浮点操作均未改善

## 展开的影响

- 关键路径
  - 整数加法的延迟为 1
  - FP 多路复用的延迟为 4

## 展开的影响

- 仅对我们的示例中的整数求和有帮助
  - 其他情况受功能单元延迟的限制
- 展开程度的影响是非线性的
  - 许多微妙的影响决定了操作的精确调度

## 增强并行性

- 多个累加器
  - 在两个不同的和中累加
    - 可以同时执行
  - 最后合并

## 翻译

- 循环内的两个乘法不再具有数据依赖性
- 允许它们流水线

```
load (%rax,%rdx.0,4) ➔ t.1a
mulq t.1a, %xmm0.0 ➔ %xmm0.1
load 4(%rax,%rdx.0,4) ➔ t.1b
mulq t.1b, %xmm1.0 ➔ %xmm1.1
addq $2,%rdx.0 ➔ %rdx.1
cmpq %rdx.1, %rbp ➔ cc.1
jg-taken cc.1
```

## 图形表示

```
mulss (%rax,%rdx,4), %xmm0
mulss 4(%rax,%rdx,4), %xmm1
addq $2,%rdx
cmpq %rdx,%rbp
jg loop
```

![](img/9bd5f6161cb6607b56d2fb964d1b8794_351_0.png)

## 图形表示

![](img/9bd5f6161cb6607b56d2fb964d1b8794_352_0.png)

## 图形表示

![](img/9bd5f6161cb6607b56d2fb964d1b8794_353_0.png)

| 函数 | 整数 + | 整数 * | 浮点 + | 浮点 F* | 浮点 D* |
|---|---|---:|---:|---:|---:|
| combine4 | 2 | 3 | 3 | 4 | 5 |
| Combine5*2 | 2 | 1.5 | 3 | 4 | 5 |
| Combine6 (U*2, P*2) | 1.5 | 1.5 | 1.5 | 2 | 2.5 |
| Latency | 1 | 3 | 3 | 4 | 5 |
| Throughput | 1 | 1 | 1 | 1 | 1 |

![](img/9bd5f6161cb6607b56d2fb964d1b8794_353_1.png)

## 再关联变换

```
void combine7(vec_ptr v, int *dest)
{
    int i;
    int length = vec_length(v), limit = length-1;
    int *data = get_vec_start(v);
    int x = IDENT;

    /* combine 2 elements at a time */
    for (i = 0; i < limit; i+=2) {
        x = x OPER (data[i] OPER data[i+1]);
    }

    /* finish any remaining elements */
    for (; i < length; i++)
        x0 = x0 OPER data[i];

    *dest = x0 OPER x1;
}
```

## 翻译

- 循环内的两个乘法不再具有数据依赖性
- 允许它们流水线

```
load (%rax,%rdx.0,4) ➔ xmm0.0
load 4(%rax,%rdx.0,4) ➔ t.1
mulq t.1, %xmm0.0 ➔ xmm0.1
mulq %xmm0.1, %xmm1.0 ➔ xmm1.1
addq $2,%rdx.0 ➔ %rdx.1
cmpq %rdx.1, %rbp ➔ cc.1
jg-taken cc.1
```

## 图形表示

%rax %rbp %rdx %xmm0 %xmm1

load
load
mul
mul
add
cmp
jg

```
movss (%rax,%rdx,4), %xmm0
mulss 4(%rax,%rdx,4), %xmm0
mulss %xmm0, %xmm1
addq $2,%rdx
cmpq %rdx,%rbp
jg loop
```

%rax %rbp %rdx %xmm0 %xmm1

## 图形表示

![](img/9bd5f6161cb6607b56d2fb964d1b8794_358_0.png)

## 图形表示

![](img/9bd5f6161cb6607b56d2fb964d1b8794_359_0.png)

| 函数 | 整数 + | 整数 * | 浮点 + | 浮点 F* | 浮点 D* |
|---|---|---|---|---|---|
| combine6 (U*2,P*2) | 1.5 | 1.5 | 1.5 | 2 | 2.5 |
| combine7 (U*2,RT) | 2 | 1.5 | 1.5 | 2 | 2.5 |
| Latency | 1 | 3 | 3 | 4 | 5 |
| Throughput | 1 | 1 | 1 | 1 | 1 |

![](img/9bd5f6161cb6607b56d2fb964d1b8794_359_1.png)


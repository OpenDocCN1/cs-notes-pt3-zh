

## 乘法

- 无符号
  $x *^{u}_{w} y = (x \cdot y) \mod 2^{w}$
- 有符号
  $x *^{t}_{w} y = U2T_{w}((x \cdot y) \mod 2^{w})$
- 给定两个位向量 $\vec{x}$ 和 $\vec{y}$
- $B2U_{w}(\vec{x}) *^{u}_{w} B2U_{w}(\vec{y})$ 与 $B2T_{w}(\vec{x}) *^{t}_{w} B2T_{w}(\vec{y})$ 相同

## 乘法

- 保持精确结果
  - 需要随着每次乘积的计算不断扩展字长
  - 在软件中由“任意精度”算术包完成

## 2的幂乘法与移位

操作数：w 位

u

k

* 2^k

真实乘积：w+k 位 u · 2^k

丢弃 k 位：w 位

UMult_w(u , 2^k)

TMult_w(u , 2^k)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_242_0.png)

## 2的幂乘法与移位

- 操作
  - u << k 给出 u * 2^k
  - 既适用于有符号也适用于无符号
- 示例
  - u << 3 == u * 8
  - u << 5 - u << 3 == u * 24
  - 大多数机器的移位和加法比乘法快得多
    - 编译器会自动生成此代码

## XDR 库中的安全漏洞

```
/*
 * Illustration of code vulnerability similar to that found in
 * Sun’s XDR library.
 */
```

## XDR 库中的安全漏洞

```
5 void* copy_elements(void *ele_src[], int ele_cnt, size_t ele_size) {
6     /*
7     * Allocate buffer for ele_cnt objects, each of ele_size bytes
8     * and copy from locations designated by ele_src
9     */
10    void *result = malloc(ele_cnt * ele_size);
11    if (result == NULL)
12        /* malloc failed */
13        return NULL;
```

## XDR 库中的安全漏洞

```
14  void *next = result;
15  int i;
16  for (i = 0; i < ele_cnt; i++) {
17      /* Copy object i to destination */
18      memcpy(next, ele_src[i], ele_size);
19      /* Move pointer to next memory region */
20      next += ele_size;
21  }
22  return result;
23 }
```

## 程序的机器级表示 I

## 大纲

- 内存和寄存器
- 建议阅读
  - Chap 3.1, 3.2, 3.3, 3.4

## 高级编程语言的特征

- 抽象
  - 生产力高
  - 可靠
- 类型检查
- 与手工编写代码一样高效
- 可以编译并在多种不同的机器上执行

## 汇编编程语言的特征

- 管理内存
- 执行计算的低级指令
- 高度机器特定

## 从编写汇编代码到理解汇编代码

- 不同的技能集
  - 转换
  - 源代码与汇编代码之间的关系
- 反向工程
  - 试图理解系统创建的过程
    - 通过研究系统
    - 通过反向工作

## 理解编译系统的工作原理

- 优化程序性能
- 理解链接时错误
- 避免安全漏洞
  - 缓冲区溢出

## C 构造

- 变量
  - 可以声明不同数据类型
- 操作
  - 算术表达式求值
- 控制
  - 循环
  - 过程调用和返回

## 代码示例

```
C code
int accum = 0;
int sum(int x, int y)
{
    int t = x+y;
    accum += t;
    return t;
}
```

## 代码示例

```
C code
int accum = 0;
int sum(int x, int y)
{
    int t = x+y;
    accum += t;
    return t;
}
```

使用命令获取
gcc -O2 -S code.c
汇编文件 code.s

```
_sum:
    pushl %ebp
    movl %esp,%ebp
    movl 12(%ebp),%eax
    addl 8(%ebp),%eax
    addl %eax, accum
    movl %ebp,%esp
    popl %ebp
    ret
```

## 历史视角

- 漫长的演进发展
  - 起源于相当原始的 16 位处理器
  - 添加了更多功能
    - 利用技术改进的优势
    - 满足对更高性能和支持更先进操作系统的需求
  - 带有提供向后兼容性的功能，这些功能已过时


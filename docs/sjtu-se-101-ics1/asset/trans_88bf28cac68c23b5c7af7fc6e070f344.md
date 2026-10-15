

先决条件

## 调试

炸弹！

Bug 与警告

调试

示例

## 示例#1

test.c: 在函数 `main' 中：
test.c:18: 警告：函数 `malloc' 的隐式声明

## 示例#2

test.c:6: 错误：在 `struct' 之前应有 `,' 或 `;'

## 示例#3

test.c:18: 错误：`j' 未声明（此函数中首次使用）

## 示例#4

test.c:18: 错误：在 `)' 标记之前应有 `;'
test.c:18: 错误：在 `)' 标记之前应有语句

## 示例#5

test.c:27: 错误：`test' 的类型冲突
test.c:4: 注意：`test' 先前的声明在此处

## 示例#1

test.c:22: 警告：此函数中 'x' 未初始化就使用

## 示例#2

test.c:16: 警告：未使用的变量 's'

## 示例#3

test.c:19: 警告：格式串的参数太少

test.c:22: 警告：此函数中 'x' 未初始化就使用

## 示例#4

test.c: 在函数 'main' 中：

test.c:24: 警告：控制流到达非 void 函数的结尾

## 示例#5

test.c: 在函数 'test' 中：

test.c:30: 警告：赋值在没有强制转换的情况下将整数转换为指针

## 这是个玩笑 ^o^

## 这是一个 "Hello world!" 程序

```
int main(void) {
    printf("hello world!\n");
    return 0;
}
```

## 这段代码如何？

```
int main(void) {
    printf("hello world!\n");
    http://ipads.se.sjtu.edu.cn/courses/ics
    return 0;
}
```

先决条件

调试

炸弹！

二进制炸弹

拆除炸弹

使用 GDB

## 拆除

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1368_0.png)

- 什么是炸弹？
  - 只是一个二进制文件
- 你应该做什么？
  - 找到钥匙并拆除炸弹！
- 你可以使用什么？
  - ICS 课程中学到的任何东西
  - 任何工具

正确钥匙 → 存活
错误钥匙 → 炸弹！

gdb 计算器
strings objdump
纸和铅笔

## 演示

- 请仔细观察！
  - 一个二进制炸弹
  - 需要一个**密码**来拆除它

## 演示

```
```text
$ ./bomb
input password: 224
bomb!...
$

$ ./bomb
input password: 123
survive!
```
```

## 黑客

## 黑客帝国：重装上阵

www.thematrix.com

先决条件

调试

炸弹！

二进制炸弹

拆除炸弹

使用 GDB

## 分步操作

- 从机器码到汇编代码

```
objdump -D bomb > asm
```

名称

objdump - 显示目标文件中的信息。

语法

objdump [-d|--disassemble]
[-D|--disassemble-all]

```
080483c4 <main>:
...
80483d5:  c7 04 24 38 85 04 08      movl    $0x8048538,(%esp)
80483dc:  e8 17 ff ff ff          call    80482f8 <printf@plt>
80483e1:  8d 45 f8                lea     0xfffffff8(%ebp),%eax
80483e4:  89 44 24 04             mov     %eax,0x4(%esp)
80483e8:  c7 04 24 48 85 04 08      movl    $0x8048548,(%esp)
80483ef:  e8 e4 fe ff ff          call    80482d8 <scanf@plt>
80483f4:  8b 45 f8                mov     0xfffffff8(%ebp),%eax
80483f7:  83 f8 7b                cmp     $0x7b,%eax
80483fa:  75 0e                   jne     804840a <main+0x46>
80483fc:  c7 04 24 4b 85 04 08      movl    $0x804854b,(%esp)
8048403:  e8 c0 fe ff ff          call    80482c8 <puts@plt>
8048408:  eb 0c                   jmp     8048416 <main+0x52>
804840a:  c7 04 24 54 85 04 08      movl    $0x8048554,(%esp)
8048411:  e8 b2 fe ff ff          call    80482c8 <puts@plt>
8048416:  b8 00 00 00 00           mov     $0x0,%eax
...
8048423:  c3                      ret
```

```
```asm
080483c4 <main>:
...
80483d5:    c7 04 24 38 85 04 08    movl    $0x8048538,(%esp)
80483dc:    e8 17 ff ff ff          call    80482f8 <printf@plt>
80483e1:    8d 45 f8                lea     0xfffffff8(%ebp),%eax
80483e4:    89 44 24 04             mov     %eax,0x4(%esp)
80483e8:    c7 04 24 48 85 04 08    movl    $0x8048548,(%esp)
80483ef:    e8 e4 fe ff ff          call    80482d8 <scanf@plt>
80483f4:    8b 45 f8                mov     0xfffffff8(%ebp),%eax
80483f7:    83 f8 7b                cmp     $0x7b,%eax
80483fa:    75 0e                   jne     804840a <main+0x46>
80483fc:    c7 04 24 4b 85 04 08    movl    $0x804854b,(%esp)
8048403:    e8 c0 fe ff ff          call    80482c8 <puts@plt>
8048408:    eb 0c                   jmp     8048416 <main+0x52>
804840a:    c7 04 24 54 85 04 08    movl    $0x8048554,(%esp)
8048411:    e8 b2 fe ff ff          call    80482c8 <puts@plt>
8048416:    b8 00 00 00 00          mov     $0x0,%eax
...
8048423:    c3                      ret
```
```


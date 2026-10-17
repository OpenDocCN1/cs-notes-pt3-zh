

## 3.3 自上而下分析

```pascal
procedure type;
begin
    if lookahead in {integer, char, num} then
        simple()
    else if lookahead = '^' then begin
        match('^'); match(id)
    end
    else if lookahead = array then begin
        match(array); match('['); simple();
        match(']'); match(of); type()
    end
    else error()
end;
```

## 3.3.4 非递归的预测分析

| 非终结符 | 输入符号 | | | |
|---|---|---|---|---|
| | id | + | * | ... |
| E | E → TE' | | | |
| E' | | E' → +TE' | | |
| T | T → FT' | | | |
| T' | | T' → ε | T' → *FT' | |
| F | F → id | | | |

## 预测分析器接受输入 `id * id + id$` 的动作

| 栈 | 输入 | 输出 |
|---|---|---|
| `$E` | `id * id + id$` | |
| `$E'T` | `id * id + id$` | `E → TE'` |
| `$E'T'F` | `id * id + id$` | `T → FT'` |
| `$E'T'F'id` | `id * id + id$` | `F → id` |
| `$E'T'` | `* id + id$` | |
| `$E'T'F'` | `* id + id$` | `T' → *FT'` |
| `$E'T'F` | `id + id$` | |
| `$E'T' id` | `id + id$` | `F → id` |

## 3.3.5 构造预测分析表

1. 对文法的每个产生式 $A \to \alpha$，执行(2)和(3)。
2. 对 FIRST($\alpha$) 的每个终结符 $a$，把 $A \to \alpha$ 加入 $M[A,a]$。
3. 如果 $\varepsilon$ 在 FIRST($\alpha$) 中，对 FOLLOW($A$) 的每个终结符 $b$（包括 $\$$），把 $A \to \alpha$ 加入 $M[A,b]$。
4. $M$ 的其它没有定义的条目都是 error。

## 多重定义的条目

| 非终结符 | 输入符号 | | | |
|---|---|---|---|---|
| | other | b | else | ... |
| stmt | stmt → other | | | |
| e_part | | | e_part → else stmt<br>e_part → ε | |
| expr | | expr → b | | |

## 习题

3.4(b)(c), 3.6(a)(b), 3.8

## 分析器对错误处理的基本目标

- 清楚而准确地报告错误的出现
- 迅速地从每个错误中恢复过来，以便诊断后面的错误，并尽量少出现伪错误
- 它不应该使正确程序的处理速度降低太多

## 非递归预测分析在什么场合下发现错误

- 栈顶的终结符和下一个输入符号不匹配
- 栈顶是非终结符A，输入符号是a，而M[A，a]是空白

## 非递归预测分析：采用紧急方式的错误恢复

发现错误时，分析器每次抛弃一个输入记号，直到输入记号属于某个指定的同步记号集合为止。

同步  
词法分析器当前提供的记号流能构成的语法结构，正是语法分析器所期望的。

## 同步记号集合的选择

- 把 FOLLOW(A) 的所有终结符放入非终结符 A 的同步记号集合。

```
if expr then
```

（then 是 expr 的一个同步记号）


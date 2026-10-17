

## School of Software
Dalian University of Technology

| 栈 | 输入 | 输出 |
|---|---|---|
| $E | id * id $ | |
| $E'T | id * id $ | E → TE' |
| $E'T'F | id * id $ | T → FT' |
| $E'T'id | id * id $ | F → id |
| $E'T' | * id $ | |
| $E'T'F* | * id $ | T' → *FT' |
| $E'T'F | id $ | |
| $E'T'id | id $ | F → id |
| $E'T' | $ | |
| $E' | $ | T' → ε |
| $ | $ | E' → ε |

| 栈 | 输入 | 输出 |
|---|---|---|
| $E | id * id $ | |
| $E'T | id * id $ | E → TE' |
| $E'T'F | id * id $ | T → FT' |
| $E'T'id | id * id $ | F → id |
| $E'T' | * id $ | |
| $E'T'F* | * id $ | T' → *FT' |
| $E'T'F | id $ | |
| $E'T'id | id $ | F → id |
| $E'T' | $ | |
| $E' | $ | T' → ε |
| $ | $ | E' → ε |

| 栈 | 输入 | 输出 |
|---|---|---|
| $E | id * id $ | |
| $E'T | id * id $ | E → TE' |
| $E'T'F | id * id $ | T → FT' |
| $E'T'id | id * id $ | F → id |
| $E'T' | * id $ | |
| $E'T'F* | * id $ | T' → *FT' |
| $E'T'F | id $ | |
| $E'T'id | id $ | F → id |
| $E'T' | $ | |
| $E' | $ | T' → ε |
| $ | $ | E' → ε |

## FIRST集合及FOLLOW集合的计算方法

### FIRST集合计算方法

- 若X→a..，则将终结符 a 加入FIRST(X)中
- 若X→ε，则将ε加入FIRST(X)中
- 若X→Y1Y2...YK，且Y属于非终结符，则将FIRST(Y)\{ε}加入到FIRST(X)中
- 若X→Y1Y2...YK，且Y1,Y2,...Yi-1都是非终结符，且Y1,Y2,...Yi-1的FIRST集合中均包含ε，则将FIRST(Yj)的所有非ε元素加入到FIRST(X)中，（j=1,2,..i）.特别地，若Y1~YK均有ε产生式，则将ε加到FIRST(X)中。

S→BA  
A→BS|d  
B→aA|bS|c  

FIRST(B)={a,b,c}  
FIRST(A)={a,b,c,d}  
FIRST(S)={a,b,c}

### FOLLOW集合计算方法

- 对文法开始符号S，置$于FOLLOW(S)中。
- 若有A→αBβ，则将FIRST(β)\{ε} 加入FOLLOW(B)中。（此处α可以为空）
- 若A→α B 或A→α B β，且 β⇒* ε （即ε 属于FIRST(β)），则将FOLLOW(A)加入FOLLOW(B)中（此处α 可以为空）。

S→BA  

FIRST(B)={a,b,c}   FIRST(A)={a,b,c,d}   FIRST(S)={a,b,c}

A→BS | d  
B→aA | bS | c  

FOLLOW(S)=?  
FOLLOW(A)=?  
FOLLOW(B)=?

## 总结

0型文法  
1型文法  
2型文法  
3型文法  

LL(1)文法  
2个函数  

上下文无关文法  
自上而下  
自下而上  

递归下降  
预测分析  
非递归的  
预测分析  

任意两个产生式A→α | β 都满足下列条件：
1、FIRST(α ) ∩ FIRST(β ) = ∅  
2、若β⇒*ε ，那么  
FIRST(α) ∩ FOLLOW(A) = ∅  

![](img/9ace97a2843cb2b456279738df7b8b56_297_0.png)

## 温故知新

E → TE'  
E' → + TE' | ε  
T → FT'  
T' → * FT' | ε  
F → ( E ) | id  

输入：id*id  

E ⇒lm TE ' ⇒lm FT 'E ' ⇒lm id T 'E ' ⇒lm id * F T 'E '  
⇒lm id * id T 'E ' ⇒lm id * id E ' ⇒lm id*id  

![](img/9ace97a2843cb2b456279738df7b8b56_298_0.png)

上下文无关文法  
自上而下  
自下而上  
最左推导  
最右推导  
LL(1)文法  
递归下降预测分析  
非递归的预测分析  
2个函数  

## 温故知新

E → TE′  
E′ → + TE′ | ε  
T → FT′  
T′ → * FT′ | ε  
F → (E) | id  

输入：id*id  

![](img/9ace97a2843cb2b456279738df7b8b56_299_0.png)

$E \Rightarrow_{rm} TE' \Rightarrow_{rm} T \Rightarrow_{rm} F T' \Rightarrow_{rm} F * F T' \Rightarrow_{rm} F * F \Rightarrow_{rm} F * id \Rightarrow_{rm} id * id$

> 从左至右读取输入字符串，如果进行最右推导。这样利用左边的符号来决定右边的产生符号展开方式，显然困难。因此，最右推导不适合使用自上而下的方式构造分析树。

## 3.4 自下而上分析

### 3.4.2 句柄

- 1. 句柄与某个产生式的右部符号串相同  
- 2. 句柄是句型的一个子串  
- 3. 把句柄归约成非终结符代表了最右推导逆过程的一步  

句型的句柄是和某产生式右部匹配的子串，并且，把它归约成该产生式左部的非终结符代表了最右推导过程的逆过程的一步。

S → aABe  
A → Abc | b  
B → d  

S ⇒<sub>rm</sub> aABe ⇒<sub>rm</sub> aAde ⇒<sub>rm</sub> aAbcde ⇒<sub>rm</sub> abbcde  

### 3.4.2 句柄

句柄性质：

S⇒rm aABe⇒rm aAde⇒rm aAbcde⇒rm abbcde  

- 1. 句柄的右边仅含终结符。  
- 2. 如果文法二义，那么句柄可能不唯一。  

例 E → E + E | E * E | (E) | id  

E⇒rm E * E  
⇒rm E * E + E  
⇒rm E * E + id₃  
⇒rm E * id₂ + id₃  
⇒rm id₁ * id₂ + id₃  

E⇒rm E + E  
⇒rm E + id₃  
⇒rm E * E + id₃  
⇒rm E * id₂ + id₃  
⇒rm id₁ * id₂ + id₃  

在句型E * E + id₃中，句柄不唯一。

### 3.4.3 用栈实现移进-归约分析

![](img/9ace97a2843cb2b456279738df7b8b56_304_0.png)

分析器的四种动作：
1. 移进动作 把下一个输入符号压栈。
2. 规约动作 分析器知道整个句柄已经完全出现在栈顶，它确定句柄的左端在栈中的位置，再决定采用哪个非终结符来代替句柄（即确定使用哪个产生式）。
3. 接受动作 分析器宣告分析成功。
4. 报错动作 分析器发现了语法错误，调用错误恢复例程。

## 例：设文法G(S)：

- (1) S → aAcBe  
- (2) A → b  
- (3) A → Ab  
- (4) B → d  

试对abbcde进行“移进一归约”分析。

![](img/9ace97a2843cb2b456279738df7b8b56_305_0.png)

![](img/9ace97a2843cb2b456279738df7b8b56_305_1.png)

## 3.4 自下而上分析

### 3.4.3 用栈实现移进-归约分析

通过移进-归约分析器在分析输入串id₁ * id₂ + id₃时动作序列来了解移进-归约分析的工作方式。

| 栈 | 输入 | 动作 |
|---|---|---|
| $ | id<sub>1</sub> * id<sub>2</sub> + id<sub>3</sub>$ | |
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |


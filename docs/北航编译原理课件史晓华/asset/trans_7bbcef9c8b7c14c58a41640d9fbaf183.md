

例:G'[E']
令I={E'→.E}
closure(I)={E'→.E, E→.E+T, E→.T, T→.T*F, T→.F, F→.(E), F→.i }

```
Procedure closure(I);
begin
    将属于I的项目加入closure(I);
    repeat
        for closure(I)中的每个项目A→α.Bβ(B∈Vₙ) do
            将B→.r(r∈V*)加入closure(I)
    until closure(I)不再增大
end
```

## B. 状态转移函数GOTO的定义:
GOTO(I,X) = closure(J)

- I: 项目集合
- X: 文法符号, X∈V
- J: 项目集合

J = { 任何形如A→αX.β的项目 | A→α.Xβ ∈ I }

closure(J):项目集J的闭包, 仍是项目集合

所以,GOTO(I,X) = closure(J) 的直观意义是:

它规定了识别文法规范句型活前缀的DFA, 从状态 I(项目集)出发,经过X弧所应该到达的状态(项目集合)

## 例：
I={E'→E. , E→E.+T} 求GOTO(I , +) =?
GOTO(I , +) = closure(J)

∵J = {E→E+.T}
∴GOTO(I , +) = {E→E+.T , T→.T*F , T→.F , F→.(E) , F→.i}

- (1) E'→.E
- (2) E'→E.
- (3) E→.E+T
- (4) E→E.+T
- (5) E→E+.T

- (6) E→E+T.
- (7) E→.T
- (8) E→T.
- (9) T→.T*F
- (10) T→T.*F

- (11)T→T*.F
- (12)T→T*F.
- (13)T→.F
- (14)T→F.
- (15)F→.(E)

- (16)F→.(.E)
- (17)F→(E.)
- (18)F→(E).
- (19)F→.i
- (20) F→i.

## LR(0)和GOTO的构造算法:
```
G'→LR(0), GOTO
Procedure ITEMSETS(G')
begin
    LR(0) := {closure({E'→.E})};
    repeat
        for LR(0)中的每个项目集I和G'的每个符号X do
            if GOTO(I , X)非空,且不属于LR(0)
            then 把GOTO(I , X)放入LR(0)中
    until LR(0)不再增大
end
```

(0) E'→E    (4) T→F
(1) E→E+T    (5) F→(E)
(2) E→T    (6) F→i
(3) T→T*F

## 例:求G'[E']的LR(0)
V={E, T, F, i, +, *, (, )}

G'[E']共有20个项目

LR(0)={I₀,I₁,I₂,...I₁₁}

由12个项目集组成:

I₀: { E'→.E
E→.E+T
E→.T
T→.T*F
T→.F
F→.(E)
F→.i }

closure({E'→.E}) = I₀

I₁: E'→E.
E→E.+T

GOTO(I₀,E) = closure({E'→E.
E→E.+T})

= I₁

I₂: E→T. T→T.*F GOTO(I₀,T) = closure({E→T. T→T.*F}) = I₂

I₃: T→F. GOTO(I₀,F) = closure({T→F.}) = I₃

I₄: F→(.E) E→.E+T E→.T T→.T*F T→.F F→.(E) F→.i GOTO(I₀,() = closure({F→(.E)}) = I₄

I₅: F→i. GOTO(I₀,i) =closure({F→i.}) = I₅

GOTO(I₀,*) = φ

GOTO(I₀,+) = φ

GOTO(I₀,)) = φ

I₀: E'→.E E→.E+T E→.T T→.T*F T→.F F→.(E) F→.i

I₁: E′→E·
  E→E·+T

I₂: E→T·
  T→T·*F

I₃: T→F.

I₆:
{ E→E·+T
  T→·T*F
  T→·F
  F→·(E)
  F→·i }

GOTO(I₁,+) = closure({E→E·+T}) = I₆
GOTO(I₁,其他符号)为空

I₇:
{ T→T·*F
  F→·(E)
  F→·i }

GOTO(I₂,*) = closure({T→T·*F}) = I₇
GOTO(I₂,其他符号)为空
GOTO(I₃,所有符号)为空

## Compiler
I₄:  F→(·E)  E→·E+T  E→·T  T→·T*F  T→·F  F→·(E)  F→·i

I₅:  F→i·

I₈:
{ F→(E·)
  E→E·+T }

GOTO(I₄,E) = closure({F→(E·), E→E·+T}) = I₈
GOTO(I₄,T) = I₂ ∈ LR(0)
GOTO(I₄,F) = I₃ ∈ LR(0)
GOTO(I₄,() = I₄ ∈ LR(0)
GOTO(I₄,i) = I₅ ∈ LR(0)
GOTO(I₄,+) = φ
GOTO(I₄,*) = φ
GOTO(I₄,)) = φ
GOTO(I₅,所有符号) = φ

I₆:  E→E+·T  T→T·*F  T→·F  F→·(E)  F→·i

I₉:
E→E+T·
T→T·*F

GOTO(I₆,T) = closure({E→E+T·, T→T·*F}) = I₉
GOTO(I₆,F) = I₃
GOTO(I₆,() = I₄
GOTO(I₆,i) = I₅

I7: T→T*.F
F→.(E)
F→.i

I10:T→T*F. GOTO(I7,F)=closure({T→T*F.})=I10
GOTO(I7,()=I4
GOTO(I7,i)=I5

I8: F→(E.)
E→E.+T

I11:F→(E). GOTO(I8,))=closure({F→(E).})=I11
GOTO(I8,+)=I6

I9: E→E+T. T→T.*F

GOTO(I9,*)=I7

GOTO(I10,所有符号)=φ, GOTO(I11,所有符号)=φ

## ③ 构造DFA
```
M = (S, V, GOTO, S₀, Z)
S = {I₀, I₁, I₂, ..., I₁₁} = LR(0)
V = {+, *, i, (, ), E, T, F}
GOTO(Iₘ, X) = Iₙ
S₀ = I₀
Z = S - {I₀} = {I₁, I₂, ..., I₁₁}
```

M的图解表示如下：

![](img/1ebd4dbc150db02388404d0c659c1fd7_377_0.png)

## 关于自动机的说明：
①除I₀以外,其余状态都是终态,从I₀到每一状态的每条路径都识别和接受一个规范句型的活前缀

如对文法句子i+i*进行规范归约所得的规范句型的活前缀都可以由该自动机识别,如:

- I₀~I₁　识别规范句型的活前缀 E+i*i
- I₀~I₆　识别规范句型的活前缀 E+i*i
- I₀~I₉　识别规范句型的活前缀 E+T*i
- I₀~I₇　识别规范句型的活前缀 E+T*i
- I₀~I₁₀　识别规范句型的活前缀 E+T*F

I0~I1 识别规范句型的活前缀E+i*i
I0~I6 识别规范句型的活前缀E+i*i
I0~I9 识别规范句型的活前缀E+T*i
I0~I7 识别规范句型的活前缀E+T*i
I0~I10 识别规范句型的活前缀E+T*F

| 步骤 | 状态栈 | 符号 | 输入串 | 动作 |
|---|---|---|---|---|
| 1 | # 0 | # | i+i*i# | 初始化，将栈顶置0状态 |
| 2 | # 0i5 | # i | +i*i# | S |
| 3 | # 0F3 | # F | +i*i# | r6 F-->i |
| 4 | # 0T2 | # T | +i*i# | r4 T-->F |
| 5 | # 0E1 | # E | +i*i# | r2 E-->T |
| 6 | # 0E1+6 | # E+ | i*i# | S |
| 7 | # 0E1+6i5 | # E+i | *i# | S |
| 8 | # 0E1+6F3 | # E+F | *i# | r6 F-->i |
| 9 | # 0E1+6T9 | # E+T | *i# | r4 T-->F |
| 10 | # 0E1+6T9*7 | # E+T* | i# | S |
| 11 | # 0E1+6T9*7i5 | # E+T*i | # | S |
| 12 | # 0E1+6T9*7F10 | # E+T*F | # | r6 F-->i |
| 13 | # 0E1+6T9 | # E+T | # | r3 T-->T*F |
| 14 | # 0E1 | # E | # | r1 E-->E+T |
| 15 | # 0E1 | # E |  | Accept |


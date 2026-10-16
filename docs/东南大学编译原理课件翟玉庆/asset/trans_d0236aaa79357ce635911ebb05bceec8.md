

## CHAPTER 4 SYNTAX ANALYSIS
## Section 5 LR parsers
## 16、规范 LR 分析表的构造

- Notes:
- 1) 每个 SLR(1) 文法都是一个 LR(1) 文法
- 2) 对于同一文法，规范 LR 分析器可能比 SLR 分析器具有更多的状态。

## CHAPTER 4 SYNTAX ANALYSIS
## Section 5 LR parsers
## 17、 LALR(lookahead-LR)

- 1) 基本思想

合并具有相同核心的 LR(1) 状态集合

Notes: (1) 合并时，GOTO 子表可以无冲突地合并，因为 GOTO 函数仅依赖于核心

(2) 合并时，ACTION 子表也可以无冲突地合并，但可能会出现错误与移/归约动作合并的情况。我们假设非错误动作

Notes: (3) 在 LR(1) 状态集合合并后，错误可能被晚些捕获，但错误最终会被捕获，事实上，它会在再移入任何输入符号之前被捕获。

Notes: (4) 合并后，可能出现归约/归约冲突。

```
S’→S
S→aBc|bCc|aCd|bBd
B→ε
C→ε
```

I0: S'→.S
S →.aBc
S →.bCc
S →.aCd
S →.bBd

I1: S'→S.

I2: S→a.Bc
S →a.Cd
B →.ε
C →.ε

I4: S→aB.c

I9: S→aBc.

I5: S→aC.d

I10: S→aCd.

I3: S→b.Bc
S→b.Cd
B→.ε
C→.ε

I6: B→ε.
C→ε.

I7: S→bB.c

I11: S→bBc.

I8: S→bC.d

I12: S→bCd.

I0: S' -> •S, $ S -> •aBc, $ S -> •bCc, $ S -> •aCd, $ S -> •bBd, $

I1: S' -> S•, $

I2: S -> a•Bc, $ S -> a•Cd, $ B -> •ε, c C -> •ε, d

I3: S -> b•Cc, $ S -> b•Bd, $ B -> •ε, d C -> •ε, c

I4: S -> aB•c, $

I5: S -> aC•d, $

I6: B -> ε•, c C -> ε•, d

I7: S -> bC•c, $

I8: S -> bB•d, $

I9: C -> ε•, c B -> ε•, d

I10: S -> aBc•, $

I11: S -> aCd•, $

I12: S -> bCc•, $

I13: S -> bBd•, $

I6-I9

{B →ε.,c C →ε.,d}

{B →ε.,d C →ε.,c}

## CHAPTER 4 SYNTAX ANALYSIS
## Section 5 LR parsers
## 17、LALR(look-ahead-LR)

2)The sets of LR(1) states having the same core

- 具有相同项目的状态但前瞻符号不同，则这些状态具有相同的核心。

Notes: 我们可以将具有相同核心的这些集合合并为一个状态集合。

## CHAPTER 4 SYNTAX ANALYSIS
## Section 5 LR parsers
## 18、 An easy, but space-consuming LALR table construction

- Input. 一个扩充文法 G`
- Output. G` 的 LALR 分析表函数 action 和 goto
- Method.
- (1) 构造 C={I₀,I₁,…Iₙ}，LR(1) 项目的集合。
- (2) 对于 LR(1) 项目集合中出现的每个核心，找到所有具有该核心的集合，并用它们的并集替换这些集合。

- Method.
- (3) 设 C`={J0,J1,...Jm} 为得到的 LR(1) 项目集合。状态 I 的分析动作由 Ji 构造。如果存在分析动作冲突，则算法无法生成分析器，且文法不是 LALR。
- (4) goto 表的构造如下。

## CHAPTER 4 SYNTAX ANALYSIS
## Section 5 LR parsers
## 18、An easy, but space-consuming LALR table construction

— (4) 如果 J 是一个或多个 LR(1) 项目集合的并集，即 J = I₁ ∪ I₂ ∪ … ∪ Iₖ，则 goto(I₁, X)、goto(I₂, X)、…、goto(Iₖ, X) 的核心相同，因为 I₁、I₂、…、Iₙ 都有相同的核心。设 K 为所有具有与 goto(I₁, X) 相同核心的项目集合的并集，则 goto(J, X) = K。

## CHAPTER 4 SYNTAX ANALYSIS
## Section 6 Using ambiguous grammars
## 1、Using Precedence and Associativity to Resolve Parsing Action Conflicts

Grammar: E→E+E|E*E|(E)|i

E→E+T|T

T→T*F|F

F→(E)|i

i+i+i*i+i


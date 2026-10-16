
## 消除左递归：

S → aL（L）

L → SL′

L′ → ,SL′ | ε

## FIRST和FOLLOW集

- FIRST(S)={a,(
- FIRST(L)={a, (
- FIRST(L’ )={, , ε}
- Follow(S)={ ) , $ }
- Follow(L)={ ) , $ }
- Follow(L’ )={ ) }

## LL(1)预测分析表

|  | ( | ) | a | , | $ |
|---|---|---|---|---|---|
| S | S->(L) |  | S->a |  |  |
| L | L->SL’ |  | L->SL’ |  |  |
| L’ |  | S-> ε |  | L’->,SL’ |  |

## FIRSTVT和LASTVT集

- **FIRSTVT (S)** = {a, (}
- **FIRSTVT (L)** = {a, (, , }
- **LASTVT (S)** = {) , a}
- **LASTVT (L)** = {) , a, , }

|  | a | ( | ) | , | $ |
|---|---|---|---|---|---|
| A |  |  | > | > | > |
| ( | < | < | = | < |  |
| ) |  |  | > | > | > |
| , | < | < | > | > |  |
| $ | < | < |  |  |  |

## 求出各非终结符的FOLLOW集

- FOLLOW(S)={ ) , $}
- FOLLOW(L)={), }

## 习题

- if a<b and c<d and e<f then
- X=1
- else X=2;
- while g<h do
- X=3

if a<b and c<d and e<f then X=1 else X=2;

# B → E₁ relop E₂

```
{ B.truelist:=makelist(nextquad);
B.falselist:=makelist(nextquad+1);
gencode('if'E₁.addr relop E₂.addr 'goto-');
gencode('goto-') }
```

+ k (j<,a,b, )

+ k+1 (j , , , )

if B and M c<d and e<f then X=1 else X=2;

```
M → ε
{M.quad:=nextquad}
M.quad=k+2
```

```
B → E₁ relop E₂
{ B.truelist:=makelist(nextquad);
  B.falselist:=makelist(nextquad+1);
  gencode('if'E₁.addr relop E₂.addr 'goto-');
  gencode('goto-') }
```

+ k+2 (j<,c,d, )

+ k+3 (j , , , )

if B and M B and e<f then X=1 else X=2;

B → B₁ and M B₂

```
{backpatch(B₁.truelist, M.quad);
B.truelist := B₂.truelist;
B.falselist:=merge(B₁.falselist, B₂.falselist);}
```

+ ■ k (j<,a,b, k+2)

+ ■ k+1 (j , , , )

+ ■ k+2 (j<,c,d, )

+ ■ k+3 (j , , , k+1)

if B and M e<f then X=1 else X=2;

M → ε

{M.quad:=nextquad}

M.quad=k+4

B → E₁ relop E₂

{ B.truelist:=makelist(nextquad);
B.falselist:=makelist(nextquad+1);
gencode('if'E₁.addr relop E₂.addr 'goto-');
gencode('goto-') }

+ - k+4 (j<,e,f, )

+ - k+5 (j , , , )

if B and M B then X=1 else X=2;

B → B₁ and M B₂
{backpatch(B₁.truelist, M.quad);
B.truelist := B₂.truelist;
B.falselist:=merge(B₁.falselist, B₂.falselist);}

+ - k (j<,a,b, k+2 )
+ - k+1 (j , , , )
+ - k+2 (j<,c,d, k+5 )
+ - k+3 (j , , , k+1 )
+ - k+4 (j<,e,f, )
+ - k+5 (j , , , k+3 )

if B then X=1 else X=2;

```
S → if B then M₁ S₁ N else M₂ S₂
{backpatch(B.truelist, M₁.quad);
backpatch(B.falselist, M₂.quad);
S . n e x t l i s t : = merge(S₂.nextlist,merge(N.nextlist,S₁.nextlist))}
```

M1.quad=k+6
M2.quad=k+8

if B then X=1 else X=2;

+ - k (j<,a,b, k+2 )
+ - k+1 (j , , , k+8 )
+ - k+2 (j<,c,d, k+4 )
+ - k+3 (j , , , k+8 )
+ - k+4 (j<,e,f, k+6 )
+ - k+5 (j , , , k+8 )
+ - k+6 (= ,1 , , x )
+ - k+7 (j , , , )
+ - k+8 (= 2, , , x )

S; while M1 g<h do M2 X=3

B → E₁ relop E₂

M1.quad=k+9

```
{ B.truelist:=makelist(nextquad);
B.falselist:=makelist(nextquad+1);
gencode('if'E₁.addr relop E₂.addr 'goto-');
gencode('goto-') }
```

M2.quad=k+11

+ ■ k+9 (j<,g,h, )

+ ■ k+10 (j , , , )

+ ■ k+11 (= ,3 , , x)

M.quad=k+9

# S → while M₁ B do M₂ S₁

M1.quad=k+9

```
{backpatch(S₁.nextlist,M₁.quad);
backpatch(B.truelist,M₂.quad);
S.nextlist:=B.falselist;
gencode('goto'M₁.quad)}
```

M2.quad=k+11

+ ■ k+9 (j<, g , h, k+11)
+ ■ k+10 (j , , , )
+ ■ k+11 (= , 3 , , x )
+ ■ k+12 (j , , , k+9 )

S; M S

M.quad=k+9

S → S₁;M S₂

```
{backpatch(S₁.nextlist, M.quad);
S.nextlist:=S₂.nextlist}
```

k+7 (j , , , k+9)

试用上述翻译方案，对句子：
while A<C and B<D do
    if A<0 then C=C+1
    else A=A+2 ;
D=A+C
进行分析，以四元式的形式输出分析结果。

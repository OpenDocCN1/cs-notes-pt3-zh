
# Chapter 8 Intermediate code generation
## Section 3 Quadruples

4. The translation scheme for addressing array elements

3) semantic variables
- ARRAY
- DIM
- PLACE
- OFFSET

4) Translation code

```
(1) A→V=E
{if (V•OFFSET=null)
    GEN(=,E • PLACE,_,V•PLACE);
else
GEN([ ]=,E•PLACE,_,V•PLACE[V•OFFSET])}
```

(2)E →E⁽¹⁾ op E⁽²⁾    {T=NEWTEMP();
    GEN(op, E⁽¹⁾•PLACE, E⁽²⁾•PLACE,T);
    E • PLACE =T}

(3)E →(E⁽¹⁾)    {E • PLACE = E⁽¹⁾•PLACE}

(4)E → V    {if (V•OFFSET=null)
    E • PLACE = V •PLACE;
else
    {T=NEWTEMP();
    GEN(= [ ], E • PLACE[V •OFFSET],_,T);
    E • PLACE =T;}}

```
(5)V →Elist]  {if (TYPE[ARRAY]<>1)
    {T=NEWTEMP();
    GEN(*,Elist•PLACE,TYPE[ARRAY],T);
    Elist •PLACE=T;}
    V •OFFSET=Elist •PLACE;
    T=NEWTEMP();
    GEN(-,HEAD[ARRAY],CONS[ARRAY],T);
    V •PLACE=T}
```

```
(6)V →i      {V •PLACE=ENTRY[i];
    V •OFFSET=null}
```

```
(7)Elist →Elist^(1),E  {T=NEWTEMP();
 k= Elist^(1)•DIM+1;
 d_k=LIMIT(Elist^(1)•ARRAY,k);
 GEN(*,Elist^(1)•PLACE, d_k,T);
 T_1=NEWTEMP();
 GEN(+,T,E•PLACE, T_1);
 Elist•ARRAY= Elist^(1)•ARRAY;
 Elist•PLACE= T_1;
 Elist•DIM=k;
```

```
(8)Elist → i[ E
{Elist•PLACE=E•PLACE;
Elist•DIM=1;
Elist•ARRAY=ENTRY(i)}
```

E.g. Let A be an array:ARRAY[1:10,1:20];
the address of the beginning of the array is a, m=1.

We can get C by the computing:
(low1*n2+low2)*m=(1*20+1)*1=21

The quadruples for X=A[I,J] are:
- (1) (*,I,20,T₁)
- (2) (+, T₁,J, T₂)
- (3) (-,a,21, T₃)
- (4) (= [ ], T₃[T₂],_, T₄)
- (5) (=, T₄,_,X)

## 5.Boolean expressions

### 1)Primary purposes of boolean expressions
- Compute logical values
- Used as conditional expressions in statements that alter the flow of control,such as if or while statements.

### 2)Grammar
- E → E and E | E or E | not E | (E) | i | Eₐ rop Eₐ

### 3).Numerical representation

(1) E→Eₐ⁽¹⁾ rop Eₐ⁽²⁾    {T=NEWTEMP();
GEN(rop, Eₐ⁽¹⁾•PLACE, Eₐ⁽²⁾•PLACE, T);
E•PLACE=T }

(2) E →E⁽¹⁾ bop E⁽²⁾    {T=NEWTEMP();
GEN(bop, E⁽¹⁾•PLACE, E⁽²⁾•PLACE, T);
E•PLACE=T }

E.g. X+Y>Z or A and (not B or C)
- (+, X, Y, T₁)    ; E+E
- (>, T₁, Z, T₂)   ; E>E
- (not, B, __, T₃) ; not E
- (or, T₃, C, T₄)  ; E or E
- (and, A, T₄, T₅) ; E and E
- (or, T₂, T₅, T₆)  ; E or E

- E.g. if A or B<D then S₁ else S₂
- (1)(jnz,A,_,(5))    ;E.true, to S₁
- (2)(j,_,_,(3))     ;E.false, look at the right of or
- (3)(j<,B,D,(5))    ;Eₐ.true, to S₁
- (4)(j,_,_,(P+1))   ; Eₐ.false, to S₂
- (5) S₁
- ......
- (P)(j,_,_,(q))     ;jump over S₂
- (p+1) S₂
- ......
- (q)the code after S₂

## 6. BackPatching

1). Functions to manipulate lists of labels related to backpatching
- MakeList(i)
  - Creates a new list containing only i, an index into the array of quadruples; makelist returns a pointer to the list it has made.
- Merge(p1,p2)
- Backpatch(p,i)

### 2).Boolean expression

#### (1)Modify the grammar
E → EᴬE | E⁰E | not E | (E) | i | Eₐ rop Eₐ

Eᴬ → E and

E⁰ → E or

#### (2)Semantic Rules
(1) E → i    {E•TC=NXQ; E•FC=NXQ+1; GEN(jnz,ENTRY(i),_,0); GEN(j,_,_,0)}

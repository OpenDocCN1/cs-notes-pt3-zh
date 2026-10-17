

## 4.3.2 Follow Sets

- nullable
  - only S’ is nullable
- FIRST
  - FIRST( ES’ ) = {num,(}
  - FIRST( +S ) = {+}
  - FIRST( num ) = {num}
  - FIRST( (S) ) = {(}, FIRST(S’) = {+, ε}
  - FIRST(S) = {num,(},
- FOLLOW
  - FOLLOW(S) = { ), $ }
  - FOLLOW(S’) = { ), $ }
  - FOLLOW(E) = { +,) , $ }

```
S → ES’
S’ → ε | +S
E → num | (S)
```

## 4.3.2 Follow Sets

# Example: the simple expression grammar.

(1) exp → exp addop term  
(2) exp → term  
(3) addop → +  
(4) addop → -  
(5) term → term mulop factor  
(6) term → factor  
(7) mulop → *  
(8) factor →(exp )  
(9) factor →number  

The First sets:
First(exp)={(,number}
First(term)={(,number}
First(factor)={(,number}
First(addop)={+,-}
First(mulop)={*}

The Follow sets:
Follow (exp)={ $,+,-,) }
Follow (addop)={(,number}
Follow (term)={$,+,-,* ,)}
Follow (mulop)={(,number}
Follow (factor)={$,+,-,* ,)}

## 4.3.3 Constructing LL(1) Parsing Tables

The table-constructing rules:

- If \(A\to\alpha\) is a production choice, and there is a derivation \(\alpha\Rightarrow^*a\beta\), where \(a\) is a token, then add \(A\to\alpha\) to the table entry \(M[A,a]\);
- If \(A\to\alpha\) is a production choice, and there are derivations \(\alpha\Rightarrow^*\varepsilon\) and \(S\Rightarrow^*\beta Aa\gamma\), where \(S\) is the start symbol and \(a\) is a token (or \($\)), then add \(A\to\alpha\) to the table entry \(M[A,a]\);

## 4.3.3 Constructing LL(1) Parsing Tables

the following algorithmic construction of the LL(1) parsing table:

Repeat the following two steps for each non-terminal A and production choice A→ α.

1. For each token a in First(α), add A→α to the entry M[A,a].
2. If ε is in First(α), for each element a of Follow(A) ( a token or $), add A→α to M[A,a].

## 4.3.3 Constructing LL(1) Parsing Tables

- **Theorem:**
  
  A grammar in BNF is LL(1) if the following conditions are satisfied.
  
  1. For every production A→α₁|α₂|···|αₙ, First(αᵢ) ∩ First(αⱼ) is empty for all i and j, 1≤i,j≤n, i≠j.
  2. For every non-terminal A such that First(A) contains ε, First(A) ∩ Follow(A) is empty.

## 4.3.3 Constructing LL(1) Parsing Tables

- algorithm for automatically generating a predictive parse table from a grammar

– FOLLOW(S) = { ), $ }  
– FOLLOW(S’) = { ), $ }  
– FOLLOW(E) = { +,) ,  
$ }

FIRST( E) = {num, (}  
FIRST(S’) = {+, ε}  
FIRST(S) = {num, (},

S → ES’  
S’ → ε | +S  
E → num | (S)

|    | num | + | ( | ) | $ |
|---|---|---|---|---|---|
| S  | S → ES’ |   | S → ES’ |   |   |
| S’ |   | S ’→ +S |   |   | S ’→ ε S’ |
| E  | E → num |   | E → (S) |   |   |

## 4.3.3 Constructing LL(1) Parsing Tables

# Example: The simple expression grammar.

exp →term exp’  
addop →+ | -  
term’→mulop factor term’| ε  
factor→(exp) | number  

exp’→addop term exp’ | ε  
term →factor term’  
mulop→*

| First Sets |
|------------|
| First(exp) = { (,number} |
| First(exp’) = { +,-,ε } |
| First(term)= {(,number} |
| First(term’) = { *, ε } |
| First(factor)= {(,number } |
| First(addop)={ + ,- } |
| First(mulop)={ * } |

| Follow Sets |
|-------------|
| Follow(exp) = {$, )} |
| Follow (exp’) = {$, )} |
| Follow (term)= {$,+,-,) } |
| Follow (term’) = {$,+,-,) } |
| Follow (factor)= {$,+,-,*,)} |
| Follow (addop)={ (,number } |
| Follow (mulop)={(,number } |

## 4.3.3 Constructing LL(1) Parsing Tables

| M[N,T] | ( | **number** | ) | + | - | * | $ |
|---|---|---|---|---|---|---|---|
| *exp* | *exp* → *term* *exp’* | *exp* → *term exp’* |  |  |  |  |  |
| *exp’* |  |  | *exp’* → ε | *exp’* → *addop term exp’* | *exp’* → *addop term exp’* |  | *exp’* → ε |
| *addop* |  |  |  | *addop* → + | *addop* → - |  |  |
| *term* | *term* → *factor term’* | *term* → *factor term’* |  |  |  |  |  |
| *term’* |  |  | *term’* → ε | *term’* → ε | *term’* → ε | *term’* → *mulop factor term’* | *term’* → ε |
| *mulop* |  |  |  |  |  | *mulop* → * |  |
| *factor* | *factor* → (*exp*) | *factor* → **number** |  |  |  |  |  |


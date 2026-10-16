I₀: [S′ →• S,#]
[S →• CC,#]
[C →• cC,c/d]
[C →• d,c/d]

I₂: [S → C• C,#]
[C →• cC,#]
[C →• d,#]

I₁: [S′ → S•,#]

I₄: [C → d•,c/d]

I₅: [S → CC•,#]

I₃: [C → c• C,c/d]
[C → • cC,c/d]
[C →• d,c/d]

I₆: [C → c• C,#]
[C →• cC,#]
[C →• d,#]

I₇: [C → d•,#]

I₈: [C → cC•,c/d]

I₉: [C → cC•,#]

对于 I₀ 中的项目 [S′ →• S,#] 和产生式 S→CC，由于 FIRST(β a)= #，则 [S→• CC,#] ∈ CLOSURE(I₀)，
同理，对于 [S→• CC,#] 和 [C→cC,c/d]，由于 FIRST(β a)=FIRST(C#)={c, d}，故 [C→• cC,c/d] 和 [C→• d,c/d] 也应属于 CLOSURE(I₀)
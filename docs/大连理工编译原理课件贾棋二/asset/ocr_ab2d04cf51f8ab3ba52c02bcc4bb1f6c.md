# 4.3 L属性定义的自上而下计算

消除左递归后文法

E → T
    R
R → + T
    R₁
R → ε
T → F
    W
W → * F
    W₁
W → ε

{R.i := T.nptr}
{E.nptr := R.s}

{R₁.i := mknode( '+', R.i, T.nptr)}
{R.s := R₁.s}
{R.s := R.i}

{W.i := F.nptr}
{T.nptr := W.s}

{W₁.i := mknode( '*', W.i, F.nptr)}
{W.s := W₁.s}
{W.s := W.i}

![](bbox=[0.639, 0.202, 0.941, 0.614])
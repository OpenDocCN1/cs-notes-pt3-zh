# 4.2.3 Left Recursion Removal and Left Factoring

The LL(1) parsing table for the new expression is given as follows:

| M[N,T] | ( | number | ) | + | - | * | $ |
|---|---|---|---|---|---|---|---|
| exp | exp → term exp′ | exp → term exp′ |  |  |  |  |  |
| exp′ |  |  | exp′ → ε | exp′ → addop term exp′ | exp′ → addop term exp′ |  | exp′ → ε |
| addop |  |  |  | addop → + | addop → - |  |  |
| term | term → factor term′ | term → factor term′ |  |  |  |  |  |
| term′ |  |  | term′ → ε | term′ → ε | term′ → ε | term′ → mulop factor term′ | term′ → ε |
| mulop |  |  |  |  |  | mulop → * |  |
| factor | factor → ( exp ) | factor → number |  |  |  |  |  |

![](bbox=[0.778, 0.772, 1.0, 1.0])

![](bbox=[0.0, 0.91, 0.09, 0.998])
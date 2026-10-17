# 3.5 LR分析器

# 例 SLR(1)文法的描述能力有限

S → V = E
S → E
V → * E
V → id
E → V

I₀:
S' → · S
S → · V = E
S → · E
V → · * E
V → · id
E → · V

I₂:
S → V · = E
E → V ·

第一项目使得
action[2, =] = s6
第二项目使得
action[2, =]为按
E→V归约，因为=是
E的一个后继符。

但是，实际不存在以E=...
开始的右句型。
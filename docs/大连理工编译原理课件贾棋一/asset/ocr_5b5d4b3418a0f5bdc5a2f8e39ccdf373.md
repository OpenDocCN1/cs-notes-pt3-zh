# 2.2 词法记号的描述与识别

# 正规定义的例子

Pascal无符号数集合，例 1946, 11.28, 63.6E8, 1.99E–6

digit → 0 | 1 | ... | 9

digits → digit digit*

optional_fraction → . digits | ε

optional_exponent → (E ( + | – | ε ) digits ) | ε

num→digits optional_fraction optional_exponent

# 简化表示

num → digit+ (.digit+)? (E(+|–)? digit+)?

简化规则：
(1) r+=rr*
(2) r?=r | ε
(3) [a-z]=a|b|c| ... |z
(4) [abc]=a|b|c
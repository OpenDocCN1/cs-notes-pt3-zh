# 语法制导翻译基本思想

而属性的计算以语义规则(semantic rules)的形式赋予由文法符号组成的产生式；

|  |  |
|---|---|---|
| F → id | F·val := id·lexval |
| T → F | T·val := F·val |
| E → T | E·val := T·val |
| E → E₁+T | E·val := E₁·val+T·val |
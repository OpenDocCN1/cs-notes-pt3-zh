# 3.5 extended notations: EBNF and syntax diagrams

+   BNF notation is sometimes extended to include special notations for repetitive and optional constructs.

+   extended BNF, or EBNF.

repetition

A → A α | β (left recursive)

A → α A | β (right recursive)

EBNF opts to use curly brackets { . . } to express repetition .

A → β{α}

A → {α} β
| Production | Semantic Rules |
|---|---|
| S→if E then S₁ | S.after=newlabel();
S.code=E.code ||
 gen('if' E.place '=' '0' 'goto' S.after) ||
 S₁.code ||
 gen(S.after ':') |
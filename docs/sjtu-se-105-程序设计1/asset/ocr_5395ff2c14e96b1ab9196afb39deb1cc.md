# Parsing the number 2

Expression:
  Term
  Expression "+" Term
  Expression "-" Term
Term:
  Primary
  Term "*" Primary
  Term "/" Primary
  Term "%" Primary
Primary:
  Number
  "(" Expression ")"
Number:
  floating-point-literal

Expression
↑
Term
↑
Primary
↑
Number
↑
floating-point-literal
↑
2
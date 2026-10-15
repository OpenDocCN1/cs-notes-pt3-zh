# Tracing the Precedence Parser

```
int main() {
Expression *readE(TokenScanner & scanner, int prec) {
Expression *readE(TokenScanner & scanner, int prec) {
Expression *readE(TokenScanner & scanner, int prec) {
Expression *exp = readT(scanner);
string token;
while (true) {
token = scanner.nextToken();
int newPrec = precedence(token);
if (newPrec <= prec) break;
Expression *rhs = readE(scanner, newPrec);
exp = new CompoundExp(token, exp, rhs);
}
scanner.saveToken(token);
return exp;
}
```

| scanner | prec | newPrec | token | exp | rhs |
| odd = 2 * n + 1 | 3 | 2 | + | • |  |

![](bbox=[0.22, 0.78, 0.28, 0.88])

![](bbox=[0.45, 0.78, 0.52, 0.88])

![](bbox=[0.68, 0.78, 0.75, 0.88])
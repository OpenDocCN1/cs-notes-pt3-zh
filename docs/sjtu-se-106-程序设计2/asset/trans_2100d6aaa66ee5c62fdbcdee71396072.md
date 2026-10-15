

## The parser.cpp Implementation

```
/*
 * Function: readT
 * Usage: exp = readT(scanner);
 * -------------------------
 * This function reads a single term from the scanner.
 */

Expression *readT(TokenScanner & scanner) {
    string token = scanner.nextToken();
    TokenType type = scanner.getTokenType(token);
    if (type == WORD) return new IdentifierExp(token);
    if (type == NUMBER) return new ConstantExp(stringToInteger(token));
    if (token != "(") error("Illegal term in expression");
    Expression *exp = readE(scanner);
    if (scanner.nextToken() != ")") {
        error("Unbalanced parentheses in expression");
    }
    return exp;
}
```

## The parser.cpp Implementation

```
/*
 * Function: precedence
 * Usage: prec = precedence(token);
 * --------------------------------
 * This function returns the precedence of the specified operator
 * token.  If the token is not an operator, precedence returns 0.
 */

int precedence(string token) {
    if (token == "=") return 1;
    if (token == "+" || token == "-") return 2;
    if (token == "*" || token == "/") return 3;
    return 0;
}
```

## Tracing the Precedence Parser

```
int main() {
    TokenScanner scanner = new TokenScanner();
    scanner.setInput("odd = 2 * n + 1");
    scanner.ignoreWhitespace();
    Expression *exp = readE(scanner);
    ...
}
```

scanner
odd = 2 * n + 1

exp

## Tracing the Precedence Parser

```
int main() {
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
| odd = 2 * n + 1 | 0 |  |  |  |  |

## Tracing the Precedence Parser

```
int main() {
Expression *readE(TokenScanner & scanner, int prec) {
Expression *readT(TokenScanner & scanner) {
string token = scanner.nextToken();
TokenType type = scanner.getTokenType(token);
if (type == WORD) return new IdentifierExp(token);
if (type == NUMBER) return new ConstantExp(stringToInteger(token));
if (token != "(") error("Illegal term in expression");
Expression *exp = readE(scanner);
if (scanner.nextToken() != ")") {
error("Unbalanced parentheses in expression");
}
return exp;
}
}
```

| scanner | type | token | exp |
| odd = 2 * n + 1 | WORD | odd |  |

## Tracing the Precedence Parser

```
int main() {
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
    scanner    prec    newPrec    token    exp    rhs
    odd ^ = 2 * n + 1    0    1    =    •
```

![](img/af430dff16b82a0fe61ce7dee05dcf9c_469_0.png)

## Tracing the Precedence Parser

```
int main() {
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
| odd = 2 * n + 1 | 1 |  |  |  |  |

![](img/af430dff16b82a0fe61ce7dee05dcf9c_470_0.png)

## Tracing the Precedence Parser

```
int main() {
Expression *readE(TokenScanner & scanner, int prec) {
Expression *readE(TokenScanner & scanner, int prec) {
Expression *readT(TokenScanner & scanner) {
string token = scanner.nextToken();
TokenType type = scanner.getTokenType(token);
if (type == WORD) return new IdentifierExp(token);
if (type == NUMBER) return new ConstantExp(stringToInteger(token));
if (token != "(") error("Illegal term in expression");
Expression *exp = readE(scanner);
if (scanner.nextToken() != ")") {
error("Unbalanced parentheses in expression");
}
return exp;
}
}
```

| scanner | type | token | exp |
| odd = 2 * n + 1 | NUMBER | 2 |  |

ID
odd


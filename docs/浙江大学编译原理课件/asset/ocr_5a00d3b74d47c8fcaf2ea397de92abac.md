# # 6.3.4 Interaction of same-level declarations

```
int gcd ( int n, int m)
{ if (m == 0) return n;
  else return gcd (m, n%m);
}
```

```
void g(void); /* function prototype declaration
*/
void f (void)
{ .....g( ) .....}
```
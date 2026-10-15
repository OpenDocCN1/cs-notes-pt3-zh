# Example (Relocation) (Hw 7.13)

(a) C code

```
1      extern int p3(void);
2      int x = 1;
3      int *xp = &x;
4
5      void p2(int y) {
6      }
7
8      void p1() {
9          p2(*xp + p3());
10     }
```
# Multiply Defined Global Symbols

```
1. /*foo1.c*/
2. int main()
3. {
4.     return 0;
5. }
```

```
1. /*bar1.c*/
2. int main()
3. {
4.     return 0;
5. }
```

```
1. /*foo2.c*/
2. int x=15213;
3. 
4. int main()
5. {
6.     return 0;
7. }
```

```
1. /*bar2.c*/
2. int x=15213;
3. 
4. void f()
5. {
6. }
```
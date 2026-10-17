# # 4.6 Static Variables

+   - static:

# ## (1) applied to an external variables or function:

limits the scope of that object to the rest of the source file, the name is invisiable outside the file.

```
static char[BUFSIZE]; /* buffer for ungetch */
int getch(void) {...}
void ungetch(int c) {...}
```

# ## (2) applied to an internal variable:

the scope is the function (as automatic variable,but it remain in existence as the program (not the function) is activated.

```
void Example()
{
 static i=1;
 printf("%d times\n", i++);
}

main()
{
 Example();
 Example();
 Example();
}
```

```
1 times
2 times
3 times
```

static variables is initialized only the first time function is entered
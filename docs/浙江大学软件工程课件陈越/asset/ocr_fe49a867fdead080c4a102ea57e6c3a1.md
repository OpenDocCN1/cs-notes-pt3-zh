# 6.3 Arrays of Structures

```
```c
#define NKEYS (sizeof keytab/sizeof(struct key))

main()
{
    int n;
    char word[MAXWORD];
    while (getword(word, MAXWORD) != EOF)
        if (isalpha(word[0]))
            if ((n = binsearch(word, keytab, NKEYS)) >= 0)
                keytab[n].count++;
    for(n=0;n<NKEYS;n++)
        if( keytab[n].count>0) printf("%4d %s\n",
            keytab[n].count,keytab[n].word);
    return 0;
}
```
```

![](bbox=[0.0, 0.0, 0.198, 1.0])
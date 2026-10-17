# 6.6 Table Lookup

symbol table management:

install(s,t)

lookup(s)

algorithm:

hash(哈希，杂凑）search: convert name into a small number which used to index into an array of pointers ( to list of names)

```
struct nlist {
    struct nlist *next;
    char name;
    char *defn;
}
```

#define HASHSIZE 101

static struct nlist *hashtab[HASHSIZE]; /*pointer table */
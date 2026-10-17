
## 6.5 Self-referential Structures

```c
/* treeprint: in-order print of tree p */
void treeprint(struct tnode *p)
{
    if (p != NULL) {
        treeprint(p->left);
        printf("%4d %s\n", p->count, p->word);
        treeprint(p->right);
    }
}
```

```c
#include <stdlib.h>

/* talloc: make a tnode */
struct tnode *talloc(void)
{
    return (struct tnode *) malloc(sizeof(struct tnode));
}

char *strdup(char *s) /* make a duplicate of s */
{
    char *p;

    p = (char *) malloc(strlen(s) + 1); /* +1 for '\0' */
    if (p != NULL)
        strcpy(p, s);
    return p;
}
```

## 6.6 Table Lookup

symbol table management:

- `install(s, t)`
- `lookup(s)`

algorithm:

hash（哈希，杂凑）search: convert name into a small number which is used to index into an array of pointers (to list of names)

```c
struct nlist {
    struct nlist *next;
    char *name;
    char *defn;
};

#define HASHSIZE 101

static struct nlist *hashtab[HASHSIZE]; /* pointer table */
```

```c
/* hash: form hash value for string s */
unsigned hash(char *s)
{
    unsigned hashval;

    for (hashval = 0; *s != '\0'; s++)
        hashval = *s + 31 * hashval;
    return hashval % HASHSIZE;
}

/* lookup: look for s in hashtab */
struct nlist *lookup(char *s)
{
    struct nlist *np;

    for (np = hashtab[hash(s)]; np != NULL; np = np->next)
        if (strcmp(s, np->name) == 0)
            return np; /* found */
    return NULL; /* not found */
}
```

```c
struct nlist *lookup(char *);
char *strdup(char *);

/* install: put (name, defn) in hashtab */
struct nlist *install(char *name, char *defn)
{
    struct nlist *np;
    unsigned hashval;

    if ((np = lookup(name)) == NULL) { /* not found */
        np = (struct nlist *) malloc(sizeof(*np));
        if (np == NULL || (np->name = strdup(name)) == NULL)
            return NULL;
        hashval = hash(name);
        np->next = hashtab[hashval];
        hashtab[hashval] = np; /* insert the new node */
    } else /* already there */
        free((void *) np->defn); /* free previous defn */
    if ((np->defn = strdup(defn)) == NULL)
        return NULL;
    return np;
}
```

## 6.7 Typedef

typedef: creating new data type name (not a new type)

purpose: (1) for portability (2) for better understanding

example:

```c
char *s;
int strcmp(char *, char *);
```

```c
typedef char *STRING;
STRING s;
int strcmp(STRING, STRING);
```

```c
int (*strcmp)(char *, char *);
```

```c
typedef int (*PFI)(char *, char *);
PFI strcmp;
```

```c
struct tnode {
    char *word;
    int count;
    struct tnode *left;
    struct tnode *right;
};
struct tnode *tp;
struct tnode node;
```

```c
typedef struct tnode *TREEPTR;
typedef struct tnode {
    char *word;
    int count;
    TREEPTR left;
    TREEPTR right;
} TREENODE;
TREEPTR tp;
TREENODE node;
```

## 6.8 Unions

union: manipulate different kinds of data in a single area of storage

example:

```c
union u_tag {
    int ival;
    float fval;
    char cval;
} u;
```

Notice: any one of these types may be assigned to u and then used in expressions, so long as the usage is consistent: the type retrieved must be the type most recently stored.

access members: `union-name.member` or `union-pointer->member`

A union is a structure in which all members have offset zero from the base.

A union may only be initialized with a value of the type of its first member.

## Chapter 7. Input and Output

Input and Output are not part of the C language, but are provided by the standard library, including a set of functions.

![](img/1879308d3bf2ec0664445e4bc0146293_173_0.png)

### 7.1 Standard Input and Output

An example: converts input to lower case

```c
#include <stdio.h>
#include <ctype.h>

main() /* lower: convert input to lower case */
{
    int c;

    while ((c = getchar()) != EOF)
        putchar(tolower(c));
    return 0;
}
```

### 7.2 Formatted Output - printf

```c
int printf(char *format, arg1, arg2, …)
```

Note:

- The printf converts, formats and prints its arguments on the standard output under the control of the format.
- It returns the number of characters printed.
- The format string contains two types of objects: ordinary characters, which are copied to the output stream, and conversion specifications, each of which causes conversion and printing of the next successive argument to printf.

# 6.2.2 Synthesized and inherited attributes

# Example 6.12

```
typedef enum {decl, type,id} nodekind;
typedef enum {integer, real} typekind;
typedef struct treenode
{nodekind kind;
struct treenode *lchild, *rchild , *sibling;
typekind dtype;
char *name;
} *Syntaxree;
```
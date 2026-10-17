
## 6.3.2 Declarations

four basic kinds of declarations:

- constant declarations,
- type declarations,
- variable declarations
- procedure/function declarations.

### type declarations

- Bind names to newly constructed types and may also create aliases for existing named types. Type names are used in conjunction with a type equivalence algorithm (perform type checking of a program)

```
type table = array [1..SIZE] of Entry  (pascal)
struct Entry        (C)
{
char * name;
 int count;
 struct Entry *next ;
};
typedef struct Entry *Entryptr;
```

### variable declarations

- bind names to data types,

- integer a, b[100];  (C declaration)

- integer a, b(100)   (FORTRAN declaration)

- Variable declarations may also bind other attributes implicitly: _the scope of a declaration_.

- an attribute of variables related to scope that is also implicitly or explicitly bound is _the allocation of memory for the declared variable_ and _the duration during execution of the allocation_ (lifetime or extent of the declaration)

### procedure/function declarations

- include explicit and implicit declarations

declarations are attached to executable instructions without explicit mention.

## 6.3.3 Scope rules and block structure

- two rules:
  - declaration before use
  - the most closely nested rule for block structure

### declaration before use

- used in C and Pascal, that requires a name be declared prior to any references to the name.

- Declaration before use permits

- the symbol table to be built as parsing proceeds.

- lookups to be performed as soon as a name reference is encountered in the code.

- If the lookup fails

- a violation of declaration before use has occurred,

- the compiler will issue an appropriate error message.

### the most closely nested rule for block structure

- A language is block structured
  - if it permits the nesting of blocks inside other blocks
  - if the scope of declarations in a block are limited to that block and other block contained in that block

```
int i, j ;
int f(int size)
{ char i, temp;
  …
  {double j;
   …
  }
  {char * j;
   …
  }
}
```

after processing the declarations of the body of f

after processing the declarations of the second nested compound statement within the body of f

after exiting the body of f (and deleting its declarations)

## 6.3.4 Interaction of same-level declarations

interaction among declarations at the same nesting level can vary with the kind of declaration and with the language being translated.

One typical requirement:
No reuse of the same name in declarations at the same level.
typedef int i;
int i;
( The above declaration will cause an error.)

How much information the declarations in a sequence at the same level have available about each other

int i = 1;
Void f(void)
{ int i = 2 , j = i+1;
... }

By the most closely nested rule, the local declaration is used, j should be 3.

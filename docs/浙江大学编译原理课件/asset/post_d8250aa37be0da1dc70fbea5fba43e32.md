
## Chapter 6 Semantic Analysis

### outline

- Attributes and attribute grammars
- Algorithms for attribute computation
- The symbol table
- Data types and type checking
- A semantic analyzer for the TINY language

## 6.3 The symbol table

- **Semantic checks** refer to properties of identifiers in the program -- their scope or type
- Need an environment to store the information about identifiers = **symbol table**
- Each entry in the symbol table contains
  - the name of an identifier
  - additional information: its kind, its type, if it is constant, ...

| NAME | KIND | TYPE | ATTRIBUTES |
|---|---|---|---|
| `foo` | fun | `int x int → bool` | extern |
| `m` | arg | int | |
| `n` | arg | int | const |
| `tmp` | var | bool | const |

## 6.3.1 The structure of the symbol table

1. linear list:
   provide easy and direct implementations of the three basic operations;
   *insert* operation is performed in constant time
   *lookup* and *delete* operation are linear time in the size of the list;
   good for a compiler implementation in which speed is not a major concern
   - a prototype
   - experimental compiler
   - an interpreter for a very small programs.

2. various search tree structures
   (binary search trees, AVL trees, B trees)
   don't provide best case efficiency;
   the delete operation is very complexity;
   less useful

3. hash tables
   all three operation can be performed in almost
   constant time;
   most frequently in practice, best choice

## 6.3.1 The structure of the symbol table

### the hash table

- a **hash function** turns the search key( the identifier name, consisting of a string of characters) into an integer hash value in the index range
- indexed by an integer range from 0 to the table size minus one
- the item corresponding to the search key is stored in the bucket at this index.

## 6.3.1 The structure of the symbol table

the hash table

- **Main problem:**
  - collision: two keys are mapped to the same index by the hash function.

## 6.3.1 The structure of the symbol table

### Collision resolution

1. **open addressing:**
   - inserting the collided new items in successive buckets.
   - cause a significant degradation in performance and make delete operation difficult.
2. **separate chaining**
   - each bucket is a linear list, collisions are resolved by inserting the new item into the bucket list.
   - it is the best scheme for compiler construction.

## 6.3.1 The structure of the symbol table

### The algorithm of the hash function

1. one simple algorithm : ignore many of the characters and to add together only the value of the first few, or the first, middle, and last, characters.

_This is inadequate for a compiler._

2. Another simple method : add up the values of all the characters.

_all permutations of the same characters cause collisions._

## 6.3.1 The structure of the symbol table

### The algorithm of the hash function

3. one good solution : repeatedly use a constant number α as a multiplying factor when adding in the value of the next character.

$h_{i+1}=αh_i+c_i \quad h_0=0$

final hash value $h=h_n \bmod size$

n is the number of characters in the name being hashed.

$h=(α^{n-1}c_1+α^{n-2}c_2+…..+αc_{n-1}+c_n) \bmod size$

The choice of α has a significant effect on the outcome.

A reasonable choice for α is a power of 2, such as 16 or 128, so that the multiplication can be performed as a shift.

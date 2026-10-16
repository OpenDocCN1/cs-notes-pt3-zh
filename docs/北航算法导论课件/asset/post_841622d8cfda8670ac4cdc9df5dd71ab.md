
## 17.4 Dynamic tables

- We might allocate space for a table, only to find out later that it is not enough. We must then reallocate the table with a larger size and copy all objects stored in the original table over into the new, larger table.
- Similarly, if many objects have been deleted from the table, it may be worthwhile to reallocate the table with a smaller size.
- We assume that the dynamic table supports the operations TABLE-INSERT and TABLE-DELETE.
  - TABLE-INSERT inserts into the table an item that occupies a single slot, that is, a space for one item.
  - Likewise, TABLE-DELETE removes an item from the table, thereby freeing a slot.

- The details of the data-structuring method used to organize the table are unimportant. It might be:
  a stack, or a heap, or a hash table, or an array

- load factor $\alpha(T)$ of a nonempty table $T$:

  $$\alpha(T) = T.num/T.size$$

- We assign an empty table (one with no items) size 0, and we define its load factor to be 1.

### 17.4.1 Table expansion

- We assume that storage for a table is allocated as an **array** of slots.
- Upon inserting an item into a full table, we can **expand** the table by allocating a new table with more slots than the old table had.
- A common heuristic allocates a new table with twice as many slots as the old one.

- If the only table operations are **insertions**, then the load factor of the table is always at least 1/2, and thus the amount of wasted space never exceeds half the total space in the table.

* T.table : a pointer to T

```
TABLE-INSERT(T, x)
1  if T.size == 0
2      allocate T.table with 1 slot
3      T.size = 1
4  if T.num == T.size
5      allocate new-table with 2 · T.size slots
6      insert all items in T.table into new-table
7      free T.table
8      T.table = new-table
9      T.size = 2 · T.size
10 insert x into T.table
11 T.num = T.num + 1
```

- The running time of TABLE-EXPANSION ?

```
TABLE-EXPANSION(T, n)
    T = NULL
    for j←1 to n
        TABLE-INSERT(T, x)
```

```
TABLE-INSERT(T, x)
1  if T.size == 0
2      allocate T.table with 1 slot
3      T.size = 1
4  if T.num == T.size
5      allocate new-table with 2·T.size slots
6      insert all items in T.table into new-table
7      free T.table
8      T.table = new-table
9      T.size = 2·T.size
10 insert x into T.table
11 T.num = T.num + 1
```

- What is the cost c_i of the i-th operation?
  - If the current table has room for the new item (or the first operation), then c_i = 1 ?
  - If the current table is full, an expansion occurs, then c_i = i ?
- The worst-case cost of an operation is O(n) ?
- The upper bound of TABLE-EXPANSION is O(n²) ?
- Correct. Not tight ?

### 17.4.1 Table expansion - aggregate analysis

- The running time of TABLE-EXPANSION ?

```
TABLE-EXPANSION(T, n)
    T = NULL
    for j ← 1 to n
        TABLE-INSERT(T, x)
```

- What is the cost cᵢ of the ith operation?

$$c_i = \begin{cases} i, & \text{if } i-1=2^k,\\ 1, & \text{otherwise.}\end{cases}$$

$$\sum_{i=1}^{n} c_i \le n + \sum_{j=0}^{\lceil\lg n\rceil}2^j \le n+2n=3n.$$

```
TABLE-INSERT(T, x)
1   if T.size = 0
2       allocate T.table with 1 slot
3       T.size = 1
4   if T.num == T.size
5       allocate new-table with 2 · T.size slots
6       insert all items in T.table into new-table
7       free T.table
8       T.table = new-table
9       T.size = 2 · T.size
10  insert x into T.table
11  T.num = T.num + 1
```

| No. | cost | T |
|---:|---:|:---|
| 1 | 1 | 🟥 |
| 2 | 2 | 🟥 🟥 |
| 3 | 3 | 🟥 🟥 🟥 ▪️ |
| 4 | 1 | ⬛ ⬛ ⬛ 🟥 |
| 5 | 5 | 🟥 🟥 🟥 🟥 🟥 ▫️ ▫️ ▫️ |
| 6 | 1 | ⬛ ⬛ ⬛ ⬛ ⬛ 🟥 ▫️ ▫️ ▫️ |

Red: 执行的插入操作次数
Gray: 空槽
Black: 有元素的槽

### 17.4.1 Table expansion - accounting method

- The running time of TABLE-EXPANSION ?

```
TABLE-EXPANSION(T, n)
    T = NULL
    for j ← 1 to n
        TABLE-INSERT(T, x)
```

- What is the cost c_i of the ith operation?

$$c_i = \begin{cases} i, & \text{if } i-1 \text{ is an exact power of 2},\\ 1, & \text{otherwise}.\end{cases}$$

$$\sum_{i=1}^{n} c_i \le n + \sum_{j=0}^{\lceil\lg n\rceil}2^j$$
$$\le n + 2n$$
$$= 3n,$$

```
TABLE-INSERT(T, x)
1   if T.size = 0
2       allocate T.table with 1 slot
3       T.size = 1
4   if T.num == T.size
5       allocate new-table with 2 · T.size slots
6       insert all items in T.table into new-table
7       free T.table
8       T.table = new-table
9       T.size = 2 · T.size
10  insert x into T.table
11  T.num = T.num + 1
```

| No. | cost | T |
|---:|---:|:---|
| 1 | 1 | 2 — total is 3: 1 for cost, 2 left for credits. |
| 2 | 2 | 1 2 |
| 3 | 3 | 0 1 2 |
| 4 | 1 | 0 1 2 2 |
| 5 | 5 | -1 0 1 1 2 |
| 6 | 1 | -1 0 1 1 2 2 |

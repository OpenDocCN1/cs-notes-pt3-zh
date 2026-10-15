

## 哪个排序算法？

| original | quicksort | mergesort | insertion | selection | sorted |
|---|---|---|---|---|---|
| lifo | find | data | data | data | data |
| fifo | fifo | fifo | fifo | exch | exch |
| data | data | find | find | fifo | fifo |
| type | exch | hash | hash | find | find |
| hash | hash | heap | heap | hash | hash |
| heap | heap | lifo | lifo | heap | heap |
| sort | less | link | link | leaf | leaf |
| link | left | list | list | left | left |
| list | leaf | push | push | less | less |
| push | lifo | root | root | lifo | lifo |
| find | push | sort | sort | link | link |
| root | root | type | type | list | list |
| leaf | list | leaf | leaf | sort | next |
| tree | tree | left | tree | tree | node |
| null | null | node | null | null | null |
| path | path | null | path | path | path |
| node | node | path | node | node | push |
| left | link | tree | left | type | root |
| less | sort | exch | less | root | sink |
| exch | type | less | exch | push | sort |
| sink | sink | next | sink | sink | swap |
| swim | swim | sink | swim | swim | swim |
| next | next | swap | next | next | tree |
| swap | swap | swim | swap | swap | type |

## Heapsort Demo

![](img/a8f1b433a70f1e5c410c8b43e41b650e_249_0.png)

click to begin demo

Starting point. Array in arbitrary order.

we assume array entries are indexed 1 to N

![](img/a8f1b433a70f1e5c410c8b43e41b650e_250_0.png)

| S | O | R | T | E | X | A | M | P | L | E |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 |

## Heap construction.

Build max heap using bottom-up method.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_251_0.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_251_1.png)

Heap construction. Build max heap using bottom-up method.

sink 5

![](img/a8f1b433a70f1e5c410c8b43e41b650e_252_0.png)

Heap construction. Build max heap using bottom-up method.

sink 5

3-node heap

![](img/a8f1b433a70f1e5c410c8b43e41b650e_254_0.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_254_1.png)

Heap construction. Build max heap using bottom-up method.

sink 4

![](img/a8f1b433a70f1e5c410c8b43e41b650e_255_0.png)

S O R T L X A M P E E
4

## Heap construction. Build max heap using bottom-up method.

sink 4

![](img/a8f1b433a70f1e5c410c8b43e41b650e_256_0.png)

3-node heap

![](img/a8f1b433a70f1e5c410c8b43e41b650e_256_1.png)

## Heapsort

Heap construction. Build max heap using bottom-up method.

sink 3

![](img/a8f1b433a70f1e5c410c8b43e41b650e_258_0.png)

| S | O | X | T | L | R | A | M | P | E | E |
|---|---|---|---|---|---|---|---|---|---|---|
|   |   | 3 |   |   | 6 |   |   |   |   |   |

## Heap construction. Build max heap using bottom-up method.

sink 3

![](img/a8f1b433a70f1e5c410c8b43e41b650e_259_0.png)

3-node heap

![](img/a8f1b433a70f1e5c410c8b43e41b650e_259_1.png)

## Heap construction. Build max heap using bottom-up method.

sink 2

![](img/a8f1b433a70f1e5c410c8b43e41b650e_260_0.png)

| S | O | X | T | L | R | A | M | P | E | E |
|---|---|---|---|---|---|---|---|---|---|---|

2

## Heap construction. Build max heap using bottom-up method.

sink 2

![](img/a8f1b433a70f1e5c410c8b43e41b650e_261_0.png)

| S | T | X | O | L | R | A | M | P | E | E |
|---|---|---|---|---|---|---|---|---|---|---|
|   | 2 |   | 4 |   |   |   |   |   |   |   |

## Heap construction. Build max heap using bottom-up method.

sink 2

![](img/a8f1b433a70f1e5c410c8b43e41b650e_262_0.png)

| S | T | X | P | L | R | A | M | O | E | E |
|---|---|---|---|---|---|---|---|---|---|---|
|   | 2 |   | 4 |   |   |   |   | 9 |   |   |

## Heap construction. Build max heap using bottom-up method.

sink 2

7-node heap

![](img/a8f1b433a70f1e5c410c8b43e41b650e_263_0.png)

S T X P L R A M O E E

## Heap construction. Build max heap using bottom-up method.

sink 1

![](img/a8f1b433a70f1e5c410c8b43e41b650e_264_0.png)

| S | T | X | P | L | R | A | M | O | E | E |
|---|---|---|---|---|---|---|---|---|---|---|


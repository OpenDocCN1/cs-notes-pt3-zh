# # (a) Runtime environment of the above program during the second call to g

| x:2 x(from f):1 | Global/static area |
|-----------------|--------------------|
|                 | Activation record of main |
| m:2 Control link Return address y:1 n:1 Control link Return address m:1 Control link Return address y:0 Free space | Activation record of call to g Activation record of call to f Activation record of call to g |
| fp sp | |
| | |
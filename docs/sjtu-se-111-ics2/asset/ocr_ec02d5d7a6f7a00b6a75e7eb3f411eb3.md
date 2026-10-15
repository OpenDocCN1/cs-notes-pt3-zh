# E Destination

```
int dstE = [
    icode in { IRRMOVL, IIRMOVL,
                IOPL} : rB;
    icode in { IPUSHL, IPOPL, ICALL,
                IRET } : RESP;
    1 : RNONE;  # Don't need register
];
// not conside cmovXX
```
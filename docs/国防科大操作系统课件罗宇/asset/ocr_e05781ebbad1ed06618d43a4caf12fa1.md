![](bbox=[0.0, 0.0, 0.12, 0.62])

```
B(amount) {
    disableInterrupt();
    R1=balance;
    R2=amount;
    R1=R1-R2;
    balance=R1;
    enableInterrupt();
};
Parend;
```
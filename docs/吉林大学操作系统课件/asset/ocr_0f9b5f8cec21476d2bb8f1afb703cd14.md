# # 管理实现SCAN算法

```
Type diskhead=MONITOR

Var busy:boolean;

headpos:0..199;
direction:(up,down);
cylinder:Array[0..199]Of condition;
count:Array[0..199]Of integer;

Define require, release:
```
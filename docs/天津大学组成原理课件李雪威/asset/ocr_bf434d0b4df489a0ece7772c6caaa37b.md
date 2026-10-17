# # Stack Smashing Attacks

```
```c
void P() {
  Q();
  ...
}
```
```

```
```c
int Q() {
  char buf[64];
  gets(buf);
  ...
  return ...;
}
```
```

```
```c
void S() {
/* Something
   unexpected */
  ...
}
```
```

![](bbox=[0.602, 0.174, 0.945, 0.804])

+   - Overwrite normal return address A with address of some other code S
+   - When Q executes `ret`, will jump to other code
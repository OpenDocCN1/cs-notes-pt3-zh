# NULL Object模式

```
Employee e=DB.getEmployee("Bob");
if (e!=null && e.isTimeToPay(today))
    e.pay();
```

![](bbox=[0.34, 0.3, 0.93, 0.68])

```
Employee e=DB.getEmployee("Bob");
if (e.isTimeToPay(today))
    e.pay();
```
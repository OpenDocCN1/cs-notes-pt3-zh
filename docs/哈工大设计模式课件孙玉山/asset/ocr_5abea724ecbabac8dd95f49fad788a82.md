# Introduction to Factory Method Pattern

| Client |
|---|
| obCar Car |
| main() |

| CarObjCreator |
|---|
| obCar Car |
| +factoryMethod: Car |

```
if (usrChoice==1)
    obCar = new Lincoln(m);
else if (usrChoice==2)
    obCar = new Cadillac(m)
else if (usrChoice==3)
    obCar = new Buick(m)
return obCar;
```

| Car |
|---|
| +buyCar() |
| +buyParts() |

| Lincoln |
|---|
| -model |
| +buyCar() |
| +buyParts() |

| Cadillac |
|---|
| -model |
| +buyCar() |
| +buyParts() |

| Buick |
|---|
| -model |
| +buyCar() |
| +buyParts() |

factoryMethod is in charge of creating objects
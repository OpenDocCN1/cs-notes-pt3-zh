# “Do-While”的通常实现方法

C代码

```
do
  Body
while ( Test);
```

goto版本

```
loop:
  Body
  if ( Test)
    goto loop
```

Body:

```
{
  语句1;
  语句2;
  ...
  语句n;
}
```
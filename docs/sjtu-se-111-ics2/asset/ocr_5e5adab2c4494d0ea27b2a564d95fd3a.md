# Simple example

| Normal loop | After loop unrolling |
|---|---|
| ```
int x;
for (x = 0; x < 100; x++)
{
    delete(x);
}
``` | ```
int x;
for (x = 0; x < 100; x+=5)
{
    delete(x);
    delete(x+1);
    delete(x+2);
    delete(x+3);
    delete(x+4);
}
``` |
```
ostream &operator<<( ostream &out, Circle &C1 )
{
    out<<"x="<<C1.x<<"  y="<<C1.y;
    out<<"  radius="<<C1.radius;
    return out;
}
```
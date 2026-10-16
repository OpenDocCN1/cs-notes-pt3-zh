```
void f(B0 *ptr)
{ptr->display();}
void main()
{B0 *p;
B1 b1;
D1 d1;
p=&b1;
fun(p);//B1::display
p=&d1;
fun(p);//D1::display
}
```
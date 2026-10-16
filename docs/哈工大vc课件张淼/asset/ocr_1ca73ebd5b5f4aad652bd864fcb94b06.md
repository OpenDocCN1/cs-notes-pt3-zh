```
```cpp
class Complex
{
double real,imag;
public: ......
}
```
```

```
```cpp
Complex a(1,2),b(3,4);
c=add(a,b);
```
```

```
```cpp
friend Complex add (const Complex &c1, const Complex &c2)
```
```

```
```cpp
Complex add (const Complex &c1, const Complex &c2)
{
Complex temp;
temp.real=c1.real+c2.real;
temp.imag=c1.imag+c2.imag;
return temp;}
```
```
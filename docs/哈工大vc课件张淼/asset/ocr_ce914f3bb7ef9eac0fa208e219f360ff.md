# 思考

```
class A
{public:
    void getX();
private:
    static int x;
};
int A::x=0;
void A::getX()
{
    cout<<x;
}

int main()
{ A a;
  a.getX();
}

cout<<this->x;
```
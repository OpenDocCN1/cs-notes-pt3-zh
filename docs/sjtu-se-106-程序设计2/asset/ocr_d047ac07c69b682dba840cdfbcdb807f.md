# Function Definition for power()

```
int power(int x, int n)
{
    if (n<0)
    {
        cout << "Illegal argument";
        exit(1);
    }
    if (n>0)
        return power(x, n-1)*x;
    else
        return 1;
}
```
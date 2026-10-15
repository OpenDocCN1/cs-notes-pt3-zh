# Converting Non-tail to Tail Recursive

+   A tail-recursive Fibonacci method can be implemented by using two auxiliary parameters for accumulating results.

auxiliary parameters!

```
int fib_aux ( int n , int next, int result)
{
    if (n == 0)
        return result;
    return fib_aux(n - 1, next + result, next);
}
```

To calculate fib(n), call fib_aux(n,1,0)
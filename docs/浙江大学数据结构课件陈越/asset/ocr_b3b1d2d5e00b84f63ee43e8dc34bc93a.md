# 如何判别

```
int check ( Tree T, int V )
{
        if ( T->flag ) {
                if ( V<T->v ) return check(T->Left, V);
                else if (V>T->v) return check(T->Right, V);
                else return 0;
        }
        else {
                if ( V==T->v ) {
                        T->flag = 1;
                        return 1;
                }
                else return 0;
        }
}
```
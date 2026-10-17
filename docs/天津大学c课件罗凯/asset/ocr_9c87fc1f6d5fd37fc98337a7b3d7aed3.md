# # Two Problems

```
int main( ) {
Time t, t2;

t.hour = 12;
t.min = 67; // can set a bad value
t.print( );

t2.print( ); // can print t2 before it has good info
cout << "\n\n";
return 0;
}
```
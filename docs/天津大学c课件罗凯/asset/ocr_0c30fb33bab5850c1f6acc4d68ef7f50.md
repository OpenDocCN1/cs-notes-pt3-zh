# # Consider

```
```cpp
int min( int n1, int n2 );
int min( int n1, float f1);
int min( float f1, int n1);
```
```

```
```cpp
int main() {
	cout << min( 2, 1 ) << endl; // calls ?
	cout << min( 2, 3.2 ) << endl; // calls ?
	cout << min( 2.5, 4 ) << endl; // calls ?
```
```

Compiler thinks of this as a double, and needs to covert it, but to what? int or float ?
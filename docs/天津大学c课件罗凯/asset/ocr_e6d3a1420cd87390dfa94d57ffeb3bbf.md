# # Different Sequences

# ## Consider seed.cpp

```
```cpp
int main() {
	cout << "Enter a seed: ";
	unsigned int seed;
	cin >> seed;
	srand(seed);
	int i = 1;
	while(i <= 5) {
		cout << rand() << endl;
		++i;
	}
	return 0;
}
```
```
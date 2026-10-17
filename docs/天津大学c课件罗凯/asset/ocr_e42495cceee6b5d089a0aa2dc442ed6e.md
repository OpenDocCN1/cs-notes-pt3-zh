# # else if chain

+   - a long `else if` chain can “walk” off the screen

```
```cpp
if ( grd > 90 )
	cout << " Grade: A \n";
else
	if ( grd > 80 )
		cout << " Grade: B \n";
	else
		if ( grd > 70 )
			cout << " Grade: C \n";
		else
			if ( grd > 60 )
				cout << " Grade: D \n";
			else
				cout << " Grade: F \n";
```
```
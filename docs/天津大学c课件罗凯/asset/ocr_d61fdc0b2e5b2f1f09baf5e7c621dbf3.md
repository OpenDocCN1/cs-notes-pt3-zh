# # Will this work?

```
```cpp
int count = 1, total = 0, input = 0;

cout << "Please enter some positive numbers that I will average \n";
cout << "Enter a negative number to signal that you are done \n";

while ( input >= 0 ) {
  cout << "# " << count << ": " ;
  cin >> input;
  total = total + input;
  count = count + 1;
}

count = count - 1;

if ( count > 0 ) {
  cout << "The total of your " << count ;
  cout << " numbers is: " << total << endl;
  cout << "The average of your " << count
  cout << " number is: << ( total / count ) << endl;
}
```
```

![](bbox=[0.611, 0.309, 0.871, 0.581])
# Review of Structures

+   - What do structures allow us to do?
+     - create a new data type that can hold multiple pieces of information (can be of different data types)

+   - What are two problems that normal variables and structures have in common?
+     - contain “garbage” information when created

```
Date today;
cout << today.day << endl;
```

+   - no error checking (program has direct access)

```
today.month = 14;
```

> classes can fix
> these problems
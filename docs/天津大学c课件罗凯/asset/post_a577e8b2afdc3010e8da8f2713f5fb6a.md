

## A Boolean Type

Example logical expressions

```cpp
bool p = true;
bool q = false;
bool r = true;

bool s = (p && q);      // false
bool t = ((!q) || r );  // true
bool u = !(r && (!q));  // false
```

## Type conversion with a bool

- Internally in memory a bool stores  
  - true as 1  
  - false as 0  

- bool ➡ int  
  - true ➡ 1  
  - false ➡ 0  

## Boolean expressions that don't look like a Boolean Expression

```cpp
int i = 11;

cout << i << endl;  // Output countdown
```

> if (i--) then  
> do again

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_286_0.png)

When will this loop finish?

- 10  
- 9  
- 8  
- …  
- 2  
- 1  
- 0  

## Short Circuit Evaluation

- A boolean expression will quit as soon as it can make an accurate decision  
- Examples:

```cpp
if ( a < b && a > c ) // and
```

only if this is **true** will we check the other

```cpp
if ( a < b || a > c ) // or
```

only if this is **false** will we check the other  

## Review of if's

- Basic if statement:

```cpp
if ( num > 0 )
    cout << num << “ is greater than 0 \n”;
```

can be one line  
or a block of lines  
with the use of { }

- if else statement:

```cpp
if ( num > 0 )
    cout << num << “ is greater than 0 \n”;
else
    cout << num << “ is not greater than 0 \n”;
```

can be one line  
or a block of lines  
with the use of { }

## BAD STYLE: Do not do this!!!

- Basic if statement:

```cpp
if ( num > 0 ) cout << num << " is greater than 0 \n";
```

- if else statement:

```cpp
if ( num > 0 ) cout << num << " is greater than 0 \n";
else cout << num << " is not greater than 0 \n";
```

## Multiple lines in a block

- **Good Code Style** for the basic if statement:

```cpp
if ( life <= 0 ) {
    cout << “Gasp......I am dead \n”;
    cout << “......goodbye cruel world..... \n”;
}
```

or

```cpp
if ( life <= 0 )
{
    cout << “Gasp......I am dead \n”;
    cout << “......goodbye cruel world..... \n”;
}
```

- Good code style for the **if else** statement:

```cpp
if ( life > 0) {
    cout << “I'm feeling pretty good \n”;
    cout << “....let's go fight some bad guys \n”;
}
else {
    cout << “Gasp......I am dead \n”;
    cout << “......goodbye cruel world..... \n”
}
```

or.......

## A little about Code Style

- The compiler does not need spaces

```cpp
specDistance=speed+time/1.5235;
```

- but for us humans it is much easier to read

```cpp
specDistance = speed + time / 1.5235;
```

....put spaces before and after operators  

## Dangling Else

- a common problem

```cpp
life = 5, energyFromFood = 8;
......
if ( life > 0 )                 // if alive
    if ( energyFromFood <= 0 )              // if hungry
        cout “wow, I’m pretty hungry. \n\n”;
else
    cout << “....go on without me....... \n\n”;
```

- From the indentation, you can see the programmer wants the else to go with the first if (if alive)

```cpp
life = 5, energyFromFood = 8;
......
if ( life > 0 )      // if alive
  if ( energyFromFood <= 0 )  // if hungry
    cout "wow, I'm pretty hungry.. \n\n";
else
  cout << "....go on without me......... \n\n";
but......
```


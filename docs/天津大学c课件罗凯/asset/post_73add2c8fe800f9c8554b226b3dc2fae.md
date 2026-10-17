

## Dangling Else

- The compiler will connect the else with the nearest if that does not have an else

```cpp
life = 5, energyFromFood = 8;

if ( life > 0 )                         // if alive
    if ( energyFromFood <= 0 )          // if hungry
        cout << "wow, I'm pretty hungry.. \n\n";
else
    cout << "....go on without me....... \n\n";

but......
```

## The fix for a Dangling Else

- use `{ }` to force the compiler to use the else as you would like it to

```cpp
life = 5, energyFromFood = 8;
......
if ( life > 0 ) {
    if ( energyFromFood <= 0)
        cout << "wow, I'm pretty hungry.. \n\n";
}
else
    cout << "....go on without me....... \n\n";
```

## else if chain

- a long `else if` chain can “walk” off the screen

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

## else if chain

- so instead it will often be written like this

```cpp
if ( grd > 90 )
    cout << " Grade: A \n";
else if ( grd > 80 )
    cout << " Grade: B \n";
else if ( grd > 70 )
    cout << " Grade: C \n";
else if ( grd > 60 )
    cout << " Grade: D \n";
else
    cout << " Grade: F \n";
```

> The purpose of the *else if* chain is to find the **one** right answer

## An alternative for simple if’s

- For simple if statements *with an assignment:*

```cpp
// num1, num2 and max are int's

if ( num1 > num2 )
    max = num1;
else
    max = num2;
```

....We can use a new operator (Conditional operator)

## Conditional Operator

```cpp
// num1, num2 and max are int's

if ( num1 > num2 )
    max = num1;
else
    max = num2;
```

could be written as

```cpp
max = ( num1 > num2 ? num1 : num2 )
```

Boolean Expression

true

false

## Conditional Operator

- Conditional Operator  
  - has three operands  
  - used for simple if statements

cout << ( num1 > num2 ? num1 : num2 ) ;

Boolean Expression true false

Do we need the ( ) ? Let's take a look at the precedence table

## Operators and order of operation
(precedence)

| Operators | Association |
|---|---|
| `( )` | left to right |
| `*`, `/`, `%` | left to right |
| `+`, `-` | left to right |
| `<<`, `>>` | left to right |
| `<`, `<=`, `>`, `>=` | left to right |
| `==`, `!=` | left to right |
| `?:` | right to left |
| `=` | right to left |

## ...and what does this do?

- What is the purpose of this code?

```cpp
if (grd == 'A')
    cout << "Excellent job, your grade is an A \n"; 
else if (grd == 'B')
    cout << "Good job, your grade is a B \n"; 
else if (grd == 'C')
    cout << "You did OK, your grade is a C \n"; 
else if (grd == 'D')
    cout << "You did poorly, your grade is a D \n"; 
else if (grd == 'F')
    cout << "You flunked, your grade is a F \n"; 
else
    cout << "Your grade has an problem \n";
```

## The Switch Statement

```cpp
switch (grd) {
    case 'A':
        cout << "Excellent job, your grade is an A \n";
        break;
    case 'B':
        cout << "Good job, your grade is a B \n";
        break;
    case 'C':
        cout << "You did OK, your grade is a C \n";
        break;
    case 'D':
        cout << "You did poorly, your grade is a D \n";
        break;
    case 'F':
        cout << "You flunked, your grade is a F \n";
        break;
    default:
        cout << "Your grade has an problem \n";
}
```

## Switch Statement

- **switch** statement can switch on
  - integers, char, bool

- **default** is optional (not required)

- **break** keyword is used to designate the end of a case

- what would be the output if grd == 'B' ?
```cpp
switch (grd) {
  case 'A':
    cout << "Excellent job, your grade is an A \n";
  case 'B':
    cout << "Good job, your grade is a B \n";
  default:
    cout << "Your grade has an problem \n";
}
```


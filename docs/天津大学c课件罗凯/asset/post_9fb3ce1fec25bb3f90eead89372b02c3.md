

## Global Scope

- Variable not defined inside a block are global variables
- A global variable can be used by any function that is defined after the global variable
  - Global variables should be avoid unless they are constant
    - For this class, only global constants are allowed
- Global variables can even be used in other program files
  - cout and cin are global variables that are defined in the iostream
- Local variables can reuse a global variables's name
  - unary scope operator :: can give access to the global variable even if the name is being reused locally

## Don’t Do This At Home Either

```cpp
int i = 1;                 // creates global

int main() {
    cout << i << endl;     // uses global
    {
        char i = 'a';      // creates local
        cout << i << endl; // prints local
        ::i = 2;           // refer to global
        cout << i << endl; // prints local
        cout << ::i << endl; // print global
    }
    cout << i << endl;     // uses ????
    return 0;
}
```

## Why do we only use global constants?

```cpp
int i = 1;        // creates global

int main() {
  .......
  i = 2;           // Change i to 2
  ......
  ......
  cout << i ;      // i displays a value of -243
  return 0;
}
// 10 other functions
```

What is the problem?

## Why do we only use global constants?

```cpp
int i = 1; // creates global

int main() {
    ......
    i = 2; // change i to 2
    ...... // ...possibly hundreds of lines
    cout << i ; // i displays a value of -243
    return 0;
}
// 10 other functions
```

problem: where did i change.... you will have to look through all of the program

## Global variables are like global bank accounts

**General Rule:** Global variables should be made **constant**

## Let’s review some names associated with functions…..

void test (int d, int e, int f);

Function Prototype
Function Declaration

int main ( )
{
int a, b, c;
...
test ( a, b, c );
}

Function Heading / Header
Function Interface

Function Body

void test ( int d, int e, int f)
{
int g, h;
...
}

Function Heading / Header
Function Interface

Function Definition

void test (int d, int e, int f);

const int TABLE_SIZE = 20;

int main ( )
{
int a, b, c;
...
test ( a, b, c );
}

void test ( int d, int e, int f)
{
int g, h;
...
}

## Parameters

## Global variable

## Local variables

## Arguments

## Parameters

## Local variables

void test (int, int, int);

int main ( )
{
int a, b, c;
...
test( a, b, c);
}

Parameter names are not required in function prototype
... but it is usually **best** to use them

void test ( int d, int e, int f)
{
int g, h;
...
}

Parameter names **are** required in the function definition

## ......enough of a review, back to new material

## Consider

```cpp
int main() {
    int number1 = promptAndReadInt();
    int number2 = promptAndReadInt();
    if (number1 > number2) {
        swap(number1, number2);
    }
    cout << "The numbers in sorted order:"
         << number1 << ", " << number2 << endl;
    return 0;
}
```

## Using

```c
void swap(int a, int b) {
  int temp = a;
  a = b;
  b = temp;
  return;
}
```

Does this function do what we want?

**Remember:** if returning nothing and the return is the last statement then the return statement is not needed

## Consider

- What we want is a parameter passing method where changes to the parameter would change the arguments

```cpp
int num1 = 5, num2 = 12;
swap(num1, num2);
cout << num1 << "  " << num2 << endl;
```

displays:

12   5

That would work!

## Reference Variables

- Special meaning of `&` when used in a variable declaration
  - create a reference variable

```cpp
int & refVar = num;
```

How about doing this ?

```cpp
& refVar = num2;    // This has another meaning
```




## One last bit......

```cpp
struct Date {
int month;
int day;
int year;
} yesterday, today, tomorrow ;
```

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_723_0.png)

// in other code
today.month = 11;
tomorrow.month = 11;

## Class Exercise

- Create a **time** structure that has hours and minutes
- Create two variables **startTime** and **endTime** and set them equal to the starting and ending time of this class

## Answer

```cpp
struct Time {
    int hour;
    int minute;
} ;
```

```cpp
Time startTime = { 9, 55 }, endTime;
endTime.hour = 11;
endTime.minute = 30;
```

## Review of Structures

- What do structures allow us to do?

## Review of Structures

- What do structures allow us to do?
  - create a new data type that can hold multiple pieces of information (can be of different data types)
- What are two problems that normal variables and structures have in common?

## Review of Structures

- What do structures allow us to do?
  - create a new data type that can hold multiple pieces of information (can be of different data types)
- What are two problems that normal variables and structures have in common?
  - contain “garbage” information when created

```cpp
Date today;
cout << today.day << endl;
```

- no error checking (program has direct access)

```cpp
today.month = 14;
```

> classes can fix
> these problems

## OOP ???

- Object <u>Oriented</u> Programming
  - towards
  - in relation to
  - concerning

## OOP ???

- Object Oriented Programming
  - towards
  - in relation to
  - concerning

or this could have been written as

- Programming using Objects

So what are Objects.....?

## Some Definitions that I want you to **memorize**

- **Object**: a logical combination of data and actions
  - Button

## Some Definitions that I want you to **memorize**

- **Object**: a logical combination of data and actions
  - Button
- **Class**: the definition of an object or the blue print of an object

## Some Definitions that I want you to **memorize**

- **Object:** a logical combination of data and actions
  - Button
- **Class:** the definition of an object or the blue print of an object
- **Instance:** a variable that is created from a class

## Comparison

- Before OOP
  - code was very closely connected
    - like a rug
- With OOP
  - program is a collection of objects that work with each other

## Comparison

- Before OOP
  - code was very closely connected
    - like a rug
- Hard to write and test
- With OOP
  - program is a collection of objects that work with each other
- Easier to write and test
  - write and test one object at a time

## Comparison

- Before OOP
  - code was very closely connected
    - like a rug
- With OOP
  - program is a collection of objects that work with each other
- Hard to write and test
- Easier to write and test
  - write and test one object at a time
- Harder to modify
  - often easier to start over
- Easier to modify
  - can swap objects
    (even at run time)

## Comparison

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_737_0.png)

- **With OOP**
  - program is a collection of objects that work with each other
  - **Easier to write and test**
    - write and test one object at a time
  - **Easier to modify**
    - can swap objects (even at run time)

## Something to think about

- What would a MP3 player object be like?
- Data:
- Actions:

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_738_0.png)

## Something to think about

- What would a MP3 player object be like?
  - Data:
    - number of songs
    - current song
    - power level
    - songs – could be objects
  - Actions:
    - play
    - pause
    - rewind
    - forward
    - on/off

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_739_0.png)


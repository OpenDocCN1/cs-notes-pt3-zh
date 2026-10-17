
## 1.10 External Variables and Scope

If the program is in several source files, and a variable is defined in file1 and used in file2 and file3, then extern declarations are needed in file2 and file3 to connect the occurrences of the variable.

### file1.c

```c
#include <stdio.h>
float rate;
main()
{
	int number;
	float total(int n);
	number = 10;
	rate = 0.98;
	printf("total = %f, number = %d\n",
		total(number), number);
}
```

### file2.c

```c
float total(int num)
{
	extern float rate;
	return rate * num;
}
```

## Chapter 2: Types, Operators, and Expressions

### 2.1 Variable Names

- letters (including ‘_’) and digits, begin with letter.
- Lower case and upper case letters are distinct.
- Keywords like if, else, int, float, etc., are reserved.

### 2.3 Constants

- int: 123
- long: 12345678l, 12345678L
- float(double): 123.4, 1.2e-2
- char: 'a', '4', '\013', '\n'
- string constant: "hello, world"

A string constant such as "hello, world" is stored as a character array terminated by '\0':

```c
'h' + 'e' + 'l' + 'l' + 'o' + ' ' + 'w' + 'o' + 'r' + 'l' + 'd' + '\0'
```

`strlen(s)` can be used to compute its length.

NOTICE!

```c
int strlen(char s[])
{
	int i;
	i = 0;
	while (s[i] != '\0') ++i;
	return i;
}
```

Enumeration constant (枚举常量):

```c
enum boolean {NO, YES};
/* NO=0, YES=1 */
enum weeks {MON=1, TUE, WED, THU, FRI, SAT, SUN}
```

### 2.4 Declarations

type var1, var2, ..., varN;

```c
int lower, upper, step;
char c, line[1000];
```

is equivalent to:

```c
int lower;
int upper;
int step;
char c;
char line[1000];
```

A variable may also be initialized in its declaration, e.g.:

```c
char esc = '\\';
int i = 0;
int limit = MAXLINE + 1;
```

The qualifier const can be applied to the declaration of any variable to specify that its value will not be changed.

```c
const double e = 2.71828;
const char msg[] = "warning.";
```

### 2.5 Arithmetic Operators

**Arithmetic operators:** `+`, `-`, `*`, `/`, `%`

- `%` produces the remainder (求余), cannot be applied to float, double.
- `/`: int/int => int;
  - 17/5 => 3;
  - 17./5 => 3.4

```c
if ((year % 4 == 0 && year % 100 != 0) || year % 400 == 0)
	printf("%d is a leap year\n", year);
else
	printf("%d is not a leap year\n", year);
```

**Precedence:**

- `*`, `/`, `%` high
- `+`, `-` low

### 2.6 Relational and Logical Operators

The relational operators: `>`, `>=`, `<`, `<=`, `==`, `!=`

**Precedence:**

- `*`, `/`, `%`
- `+`, `-`
- `>`, `>=`, `<`, `<=`
- `==`, `!=`
- `||`

Logical operators: `&&` (与), `||` (或), `!` (非)

```c
i < lim - 1 && (c = getchar()) != '\n' && c != EOF
(c = getchar()) != '\n'
!valid   /* 等价于 valid == 0 */
```

Result of logical expression: true ---- 1; false ---- 0;  
当作逻辑判断时：非0 ---- true；0 ---- false；

![](img/1879308d3bf2ec0664445e4bc0146293_34_0.png)

### 2.7 Type Conversions

char < short int < int < unsigned < long < unsigned long < float < double

**Example 1:**

```c
int atoi(char s[])
{
	int i, n;
	n = 0;
	for (i = 0; s[i] >= '0' && s[i] <= '9'; ++i)
		n = 10 * n + (s[i] - '0');
	return n;
}
```

**Example 2:**

```c
int lower(int c)
{
	if (c >= 'A' && c <= 'Z')
		return c + 'a' - 'A';
	else
		return c;
}
```

### 2.8 Increment and Decrement Operators

(increment operator) `++`: adds 1 to its operand (自增)  
(decrement operator) `--`: subtracts 1 from its operand (自减)

```c
int i = 3;
i++; /* i = i + 1 */
```

`i++` and `++i` are different (also `i--`, `--i`).

If n is 5, then:

```c
x = n++; /* n = 6, x = 5 */
```

but:

```c
x = ++n; /* n = 6, x = 6 */
```

```c
void squeeze(char s[], int c)
{
	int i, j;
	for (i = j = 0; s[i] != '\0'; i++)
		if (s[i] != c) s[j++] = s[i];
	s[j] = '\0';
}
```

Equivalent to:

```c
if (s[i] != c) { s[j] = s[i]; j++; }
```

**Example 2:**

```c
if (c == '\n') { s[i] = c; ++i; }
if (c == '\n') s[i++] = c;
```

**Example 3:**

```c
/* strcat: concatenate t to end of s; s must be big enough */
void strcat(char s[], char t[])
{
	int i, j;
	i = j = 0;
	while (s[i] != '\0') i++;
	while ((s[i++] = t[j++]) != '\0');
}
```

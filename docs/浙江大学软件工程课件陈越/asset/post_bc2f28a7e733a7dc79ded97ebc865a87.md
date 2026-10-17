
# Chapter 7. Input and Output

Input and Output are not part of C language, but provided by standard library, including a set of functions.

![](img/caa6e55d367968a29a6a558fa69d0413_510_0.png)

## 7.1 Standard Input and Output

character input and output:

int getchar(void) /* read a character from the standard input */
int putchar(int) /* put a character on the standard output */

Notion:

- 1 input and output can be redirected. such as
- prog < infile
- prog > outfile
- prog | anotherprog

2 Each source file that refers to an input/output library must contain the line
#include <stdio.h>

### An example: converts input to lower case

```
#include <stdio.h>
#include <ctype.h>
main() /* lower: convert input to lower case */
{ int c;
while((c = getchar())!=EOF)
putchar(tolower(c));
return 0;
}
```

## 7.2 Formatted Output-Printf

int printf(char *format, arg1, arg2, ...)

Notion:

- ➢ The printf converts, formats and prints its arguments on the standard output under the control of the format.
- ➢ It returns the number of characters printed.
- ➢ The format string contains two types of objects: ordinary characters, which are copied to the output stream, and conversion specification, each of which causes conversion and printing of the next successive argument to printf.

![](img/caa6e55d367968a29a6a558fa69d0413_513_0.png)

## 7.3 Variable-length Argument Lists

The proper declaration for printf is

```
int printf(char *fmt, ...)
```

where the ... means that the number and types of these arguments may vary. The ... can only appear at the end of an argument list.

minprintf is a simple version of printf

```
#include <stdarg.h>

void minprintf(char *fmt, ...)
{
    va_list ap;
    char *p, *sval;
    int ival;
    double dval;
```

![](img/caa6e55d367968a29a6a558fa69d0413_516_0.png)

```
va_start(ap, fmt);
for(p=fmt; *p; p++) {
    if(*p!='%') {
        putchar(*p);
        continue;
    }
    switch(*++p) {
        case 'd': ival = va_arg(ap,int);
            printf("%d", ival);
            break;
        case 'f': dval=va_arg(ap,double);
            printf("%f", dval);
            break;
```

![](img/caa6e55d367968a29a6a558fa69d0413_517_0.png)

```
case 's' : for (sval = va_arg(ap,char *); *sval; sval++)
                    putchar(*sval);
                    break;
                default: putchar(*p);
                    break;
            }
        }
        va_end(ap);
    }
```

## 7.4 Formatted Input-Scanf

```
int scanf(char *format, ...)
int sscanf(char *string, char *format, arg1, arg2, ...);
```

- 1. scanf reads characters from the standard input, interprets them according to the specification in format.
- 2. sscanf is like scanf does, but from string, not from standard input
- 3. the format strng is just like printf, only for ordinary characters (not %), which are expected to match the next non-white space character of the input stream.

eg1: int day, year;
      char monthname[20];
      scanf("%d %s %d", &day, &monthname, &year);

eg2: int a, b, c;
      char s[] = “3 4 5 6 7”;
      sscanf(s, “%d %*d %*d %d %d”, &a, &b, &c);
      The result is a==3  b==6 and c==7

SEE OLD 13-14

![](img/caa6e55d367968a29a6a558fa69d0413_519_0.png)

## 7.5 File Access

The general steps for a file operation:
1 Open the file
2 Do operations on the file by file pointer.
3 Close a file

In C language, files are accessed by file pointers, which are declared as:
FILE *fp;

During the first step, we can use a fopen to make fp points to the file we want to access.
fp = fopen("data", "r");
or
if((fp=fopen("data", "r")) !=NULL)

![](img/caa6e55d367968a29a6a558fa69d0413_520_0.png)

FILE *fopen(char *filename, char *mode);
int fclose(FILE *fp);

- 1 The filename can include full path, just like:
- fp = fopen("c:\\system\\t.dat","r");

- 2 The mode can be
- "r": read only
- "w": write only
- "a": append only

If the system distinguish between text and binary files, for the latter, a "b" must be appended to the mode string.
fp = fopen("t.dat","rb");

- 3 When operations finished, the file should be closed.
- fclose(fp);

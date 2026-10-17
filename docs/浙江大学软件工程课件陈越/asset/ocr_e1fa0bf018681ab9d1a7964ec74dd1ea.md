# 7.3 Variable-length Argument Lists

```
case ‘s’ : for (sval = va_arg(ap,char *); *sval; sval++)
                    putchar(*sval);
                    break;
                default: putchar(*p);
                    break;
            }
        }
        va_end(ap);
    }
```
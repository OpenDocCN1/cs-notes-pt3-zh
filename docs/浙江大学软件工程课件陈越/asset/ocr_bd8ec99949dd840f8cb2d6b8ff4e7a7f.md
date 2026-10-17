# 第四章　程序流程控制

例5：根据整型变量 dayoftheweek(0-6) 值输出其表示的星期几的英语单词。

```
（无break语句）
Switch(dayoftheweek)
{
    case 0: cout<< “Sunday”；
    case 1: cout<< “Monday”；
    case 2: cout<< “Tuesday”；
    case 3: cout<< “Wednesday”；
    case 4: cout<< “Thursday”；
    case 5: cout<< “Friday”；
    case 6: cout<< “Saturday”；
    default:cout<< “Unknown week day”；
}
```
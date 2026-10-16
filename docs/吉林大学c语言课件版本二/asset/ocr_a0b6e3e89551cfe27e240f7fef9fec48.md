```
case 2: switch ( sort ){
    case 0: com_real(); \\翻译小数
        s = 3 ;
        break ;
    case 2: s = 4; \\翻译整数时遇到空白字符
        intflag = false ;
        break ;
    case 1: com_error(3); \\存在两个以上小数点
        break;
    case 3: com_error(4); \\遇到非法字
    }
    break;
```
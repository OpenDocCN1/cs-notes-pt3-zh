```
case 1: switch (sort){
    case 0: com_integer(); // 翻译整数
        break ;
    case 1: s = 2;   //翻译整数时遇到小数点
        break ;
    case 2: s = 4; //翻译整数时遇到空白字符
        break ;
    case 3: com_error(2); //翻译整数遇其它字符
}
break;
```
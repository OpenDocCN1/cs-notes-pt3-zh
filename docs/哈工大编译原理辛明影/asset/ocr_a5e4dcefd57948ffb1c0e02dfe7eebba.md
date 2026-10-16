```
procedure RECOGID(CH, TOKEN);
{ WORD:= ' ';
    WORD:=WORD||CH;
Repeat {
    call GETCH(CH);
    if CH是字母或数字 then
    WORD:=WORD||CH; } until CH!=字母或数字;
if CH是非法的字符 then
    call PRINTERR('非法字符')
else 列计数-1;
if WORD 是关键字
    then TOKEN:=(关键字词类编码,_)
else { call LOOPUP(WORD,'标识符',ENTRY)
    TOKEN:=(标识符字词类编码,ENTRY)};
    Return };
```

识别标识符；
输入：CH中含标识符的首字母；
输出：TOKEN(二元式形式)；
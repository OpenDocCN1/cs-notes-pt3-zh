# 消息框风格

+   □ 以MB_开始的常数组合代表消息框的风格
+   ■ 多种风格之间用 “|”分隔

```
if(IDOK == MessageBox(
    NULL,
    "是否退出本程序？ ",
    "退出",
    MB_OKCANCEL|
    MB_ICONQUESTION))

MessageBox(NULL,"再见！ ","退出",MB_OK);
```
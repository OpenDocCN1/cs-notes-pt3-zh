# 5.2.5 与电话整合

3、发送消息

对支持jQuery Mobile的智能手机，可以安全地使用sms://协议。

发送消息的语法是sms://[<destination number>][?parameters] 方括号表示可选，其参数格式与发送电子邮件一样。例如：

```
<a href="sms://">Send an SMS</a>
```

```
<a href="sms://?
body=Visit%20the%20best%20site%20at%20http://mobilex
web.com">Invite a friend by SMS<a>
```

```
<a href="sms://+3490322111">Contact us by SMS</a>
```

```
<a href="sms://+3490322111?
body=Interested%20in%20Product%20AA2">More info for
product AA2</a>
```

用户点击发送消息链接时，只是打开编辑短消息的窗口，相应字段也已填充，用户必须手动完成整个过程。
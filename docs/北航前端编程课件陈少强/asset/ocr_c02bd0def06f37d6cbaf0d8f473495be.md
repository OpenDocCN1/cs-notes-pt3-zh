# 5.2.5 与电话整合

2、发送电子邮件

需要使用mailto协议，语法是：

```
mailto:<destination email>[?parameters]
```

方括号表示可选参数。

不同的设备支持不同的参数，但基本上都包含cc（抄送）、bcc（暗送）、subject（标题）以及body（信件内容）参数。

参数以URL格式(key=value&key=value)定义，值必须经过URI编码。

例如：

```
<a href="mailto:info@mobilexweb.com">Mail us</a>
<a href="mailto:info@mobilexweb.com?subject=Contact%20from%20mobile">Mail us</a>
<a href="mailto:info@mobilexweb.com?subject=Contact&body=This%20is%20the%20body">Mail us</a>
```

通常，用户点击发送电子邮件链接时，支持的手机将打开发送邮件应用，相应字段也已填充。
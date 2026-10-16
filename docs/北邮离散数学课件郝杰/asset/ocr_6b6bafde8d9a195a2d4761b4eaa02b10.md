# 邮件格式：多媒体扩展

+   - MIME: multimedia mail extension, RFC 2045, 2056
+   - 在邮件头增加字段，说明媒体数据的类型

MIME版本
数据编码方法
多媒体数据类型、子类型、相关参数
已编码的数据

```
From: alice@crepes.fr
To: bob@hamburger.edu
Subject: Picture of yummy crepe.
MIME-Version: 1.0
Content-Transfer-Encoding: base64
Content-Type: image/jpeg

base64 encoded data .....
.....................
......base64 encoded data
```
# telnet程序：辅助了解其他应用层协议

+   使用TELNET协议连接到远程主机

+   C:> telnet pop.126.com 110

```
+OK Welcome to coremail Mail Pop3 Server <126coms[f7aa0ed0270c139a0807240dd70090 6bs]>
user test0318
+OK core mail
pass 123456
+OK 2 message(s) [14732 byte(s)]
list
+OK 2 14732
1 13403
2 1329
.
retr 2
+OK 1329 octets
Received: from mail.bupt.edu.cn (unknown [211.68.71.7])
    by mx1 <Coremail> with SMTP id H8nowLDbb_JKLoJNh ybVCA--.37S2;
    Thu, 17 Mar 2011 23:52:42 +0800 (CST)
Received: from localhost (localhost.localdomain [127.0.0.1])
    by mx3.bupt.edu.cn <Postfix> with SMTP id F1D5A1BD77
    for <test0318@126.com>; Thu, 17 Mar 2011 23:52:48 +0800 (CST)
```
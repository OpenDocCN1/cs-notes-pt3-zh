# 如何注册域名？

+   例子： 你刚刚创建了一个公司 “Network Utopia”

+   在域名管理机构(如Network Solutions)注册域名networkutopia.com

+   - 向域名管理机构提供你的权威域名解析服务器的名字和IP地址
+   - 域名管理机构向com顶级域名解析服务器中插入两条记录

```
(networkutopia.com, dns1.networkutopia.com, NS)
(dns1.networkutopia.com, 212.212.212.1, A)
```

在权威域名解析服务器中为www.networkutopia.com加入Type A记录，为networkutopia.com加入Type MX记录
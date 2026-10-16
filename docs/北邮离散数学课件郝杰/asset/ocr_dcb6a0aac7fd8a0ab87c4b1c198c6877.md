# DNS的安全性问题

+   - 名字服务器易受攻击，名字数据库被非法主机修改
+     - DNS伪冒(spoofing)
+     - DNS缓存毒化(Cache poisoning)
+     - DOS(Denial of Service)、缓存溢出(Buffer overrun)、重放(Replay)攻击...
+   - 改进策略：DNSSEC
+     - RFC 4033
+     - 数字签名、公共密钥
+       - 对DNS请求/应答消息进行身份认证
# Public Key Infrastructure (PKI)

+   - PKI（Public Key Infrastructure）是一种公钥基础设施，用来发布和管理公钥。
+   - 数字签名中的公钥可以使用PKI的证书获取（不必使用copy的方式分发给需要使用的用户），用户的公钥连同其他信息被封装为证书。
+   - 用户的证书使用一个公共的服务器CA (Certificate Authorities)发布，并对证书签名，以保证证书本身的可信。
+   - 证书由发布，CA可理解为一个server用来保存、管理和发放证书。
# NFS安装协议

+   - 建立client与server之间的初始联系
+   - 安装参数包括
+     - 远程待安装目录
+     - 服务器名
+   - 安装请求被映射为对应的RPC调用,并传给远程server
+   - 服务器端的export list指明可被安装目录列表,以及可对其执行安装操作的clients
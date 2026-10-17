# Windows 2000/XP邮件槽-1

+   - 有关的API如：
+     - **CreateMailslot**服务器方创建邮件槽，返回其句柄；
+     - **GetMailslotInfo**服务器查询邮件槽的信息，如：消息长度、消息数目、读操作等待时限等；
+     - **SetMailslotInfo**服务器设置读操作等待时限；
+     - **ReadFile**服务器读邮件槽；
+     - **CreateFile**客户方打开邮件槽；
+     - **WriteFile**客户方发送消息；

在邮件槽的所有服务器句柄关闭后，邮件槽被关闭。这时，未读出的报文被丢弃，所有客户句柄都被关闭。
# Windows NT

+   - 邮件槽(mailslot)：驻留在OS核心，不定长数据块（报文），不可靠传递
+   - 通常采用client-server模式：单向的，从client发往server；server负责创建邮件槽，它可从邮件槽中读消息；client可利用邮件槽的名字向它发送消息；
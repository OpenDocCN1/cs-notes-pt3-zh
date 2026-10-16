# BitTorrent (2)

# 获取chunk

+   - 给定任一时刻，不同的节点持有文件的不同chunk集合
+   - 节点(Alice)定期查询每个邻居所持有的chunk列表
+   - 节点发送请求，请求获取缺失的chunk
+     - 稀缺优先

# 发送chunk: tit-for-tat

+   - Alice向4个邻居发送chunk: 正在向其发送Chunk，速率最快的4个
+     - 每10秒重新评估top 4
+   - 每30秒随机选择一个其他节点，向其发送chunk
+     - 新选择节点可能加入top 4
+     - "optimistically unchoke"
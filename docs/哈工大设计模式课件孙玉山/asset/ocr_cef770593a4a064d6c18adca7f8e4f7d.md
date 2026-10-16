# Key Technologies of Cloud Computing

+   - **Master节点功能**
+     - 存储元数据
+     - 文件系统目录管理与加锁
+     - 与 **ChunkServer** 进行周期性通信
+       - 发送指令，搜集状态，跟踪数据块的完好性
+     - 数据块创建、复制及负载均衡
+       - 对ChunkServer的空间使用和访问速度进行负载均衡，平滑数据存储和访问请求的负载
+       - 对数据块进行复制、分散到ChunkServer中
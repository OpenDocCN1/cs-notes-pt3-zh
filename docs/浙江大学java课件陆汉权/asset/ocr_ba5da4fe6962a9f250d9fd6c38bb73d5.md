# # DataOutputStream流类

DataOutputStream类文件中写操作步骤：
1. 为磁盘文件建立File类对象
2. 为该File对象建立FileOutputStream类流对象，建立其与磁盘文件的连接
3. 为FileOutputStream类对象
   - 建立DataOutputStream类对象
   - 利用DataOutputStream类的writeInt(), writeFloat(), writeDouble(), writeBoolean()等方法分别向文件中写入整型、单精度型、双精度型、布尔型等数据
4. 写入操作完成后，利用close()方法将流关闭，断开与磁盘文件的联系
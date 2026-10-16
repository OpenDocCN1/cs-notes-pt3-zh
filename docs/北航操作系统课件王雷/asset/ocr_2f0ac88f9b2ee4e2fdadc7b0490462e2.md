# 传输时间

+   - Tt是指把数据从磁盘读出，或向磁盘写入数据所经历的时间，Tt的大小与每次所读/写的字节数b，旋转速度r以及磁道上的字节数N有关
+   - Tt=b/(rN)
+     - Transfer size (usually a sector): 512B - 1KB per sector
+     - Rotation speed: 3600 RPM to 15000 RPM
+     - Typical values: 2 to 50 MB per second
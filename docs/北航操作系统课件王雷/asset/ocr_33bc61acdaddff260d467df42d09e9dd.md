# 驱动程序

+   - 系统卷中引导扇区中的代码负责执行Ntlder。
+   - Ntlder从系统卷中读取Boot.ini文件，把计算机的引导选项显示给用户。Boot.ini指定分区名为 mult(0)disk(0)rdisk(0)partition(1)的形式。
+   - Ntlder把Boot.ini中用户指定的项转换为正确的引导分区，然后将Windows Server 2003系统文件（从注册表、Ntoskrnl.exe、引导驱动程序开始）装入内存，继续引导过程。
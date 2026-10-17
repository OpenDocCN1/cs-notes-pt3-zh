# # Writer和Reader

以字符流方式向文件写入或从文件中读取数据，可以使用Writer和Reader类及其子类。

Writer和Reader类都是抽象类，不能建立它们的对象，所以只能通过它们子类对象对文件进行操作。常用的Writer类的子类包括FileWriter类和BufferedFileWriter类。

FileWriter类构造方法如下：

+   ◆FileWriter(String fileName):

参数fileName表示带路径的磁盘文件名。

+   ◆FileWriter(File file):

参数file表示为磁盘文件所建立的File对象名。

注：使用FileWriter进行文件操作时，为了减少磁盘读写次数，常常使用具有缓冲功能的BufferedWriter类。
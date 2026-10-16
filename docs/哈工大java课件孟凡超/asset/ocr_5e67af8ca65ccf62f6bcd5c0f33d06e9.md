# 对话框、标准对话框与文件对话框

# 文件对话框(JFileChooser)

# 构造方法：

JFileChooser();
JFileChooser(File currentDirectory);
JFile(String currentDirectoryPath);

# 刚刚创建的文件对话框是不可见的，可以调用以下方法显示：

showOpenDialog(Component parent);
showSaveDialog(Component parent);
showDialog(Component parent, String appoveButtonText);
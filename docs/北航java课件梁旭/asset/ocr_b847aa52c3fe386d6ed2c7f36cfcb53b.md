# 把Java程序打包成可执行文件

+   - 编译好的java项目，在WINDOWS下可以这样打包与执行：
+   - 1、工程目录设置为 `$proj`
+   - 2、代码文件放到 `$proj\filename`（代码所在文件夹，代码文件.java中要有 `package **` 语句）。
+   - 3、用记事本创建并设置 manifest.mf 文件，放到目录：`$proj\manifest.mf`
+     - 内容如下：`Main-Class: filename.Frame1<回车>`
+     - 格式为：`Main-Class:` 可执行主类**全名**（包含**包名**）
+   - 4、创建并设置批处理文件（用记事本），放到目录：`$proj\play.bat`先编译，后打包，再运行。
+     - 内容如下：
+       ```bat
+       @echo off
+       javac filename \\*.java
+       jar cvfm filename.jar manifest.mf filename
+       java -jar filename.jar
+       @echo on
+       ```
+   - 5、把得到的filename.jar拷贝到任何地方都可以双击运行了。

```
```bat
@echo off
javac filename \\*.java
jar cvfm filename.jar manifest.mf filename
java -jar filename.jar
@echo on
```
```
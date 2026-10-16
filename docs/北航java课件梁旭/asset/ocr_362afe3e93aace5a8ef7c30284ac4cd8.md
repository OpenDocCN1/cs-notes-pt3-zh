# 属性列表解释：

**CODE** = *appletFile*  
　　指明需要运行的Applet类文件（.class文件），该文件是与 *codebase* URL相关的。

**WIDTH** = *pixels*　**HEIGHT** = *pixels*  
　　Applet在浏览器中所显示的高度和宽度（以象素为单位）。

**ARCHIVE** = *archivelist* [*File1, File2, ...*]  
　　给出了Applet类及其运行时所需的类所在的卷文件名。

**CODEBASE** = *codebaseURL*  
　　指明Applet类文件所在URL根目录，在Applet类中，方法getCodeBase()可以获取该属性。如果这个属性没有指明，那么Applet类文件必须与包含它的HTML页面在同一个地方，方法getCodeBase()返回的值与getDocumentBase()相同。

**NAME** = *appletInstanceName*  
　　给出了Applet类运行时的实例名，这使得同处于一个页面的不同Applet之间能够相互通信。方法getAppletContext()可以得到同一个页面中其它Applet类。
# 4. Case Study

+   - Firstly, parse method of an instance of the Input class is invoked:
+     void parse(String file, LineStorage line_storage)

The parse method reads the data from the file. For each line in that file, it creates a new line in the LineStorage by invoking its addEmptyLine method. To add words to the new line Input object invokes addWord method on LineStorage. The iterative nature of this process is symbolized in the diagram with * sign in the front of the addWord method name.
```
CREATE UNIQUE INDEX SC_INDEX
ON SC (SNO DESC, CNO ASC);
```

即：对选课文件SC按学号属性降序、按课程号属性升序建立索引文件。
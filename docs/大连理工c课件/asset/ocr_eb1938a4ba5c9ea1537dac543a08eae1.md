# # 9.4 文件流

打开一个已有文件准备读入数据的操作  
ifstream infile;  
infile.open( "datafile.dat" , ios::in );

准备向文件写数据的操作  
ofstream outfile( "D:\\newfile.dat" , ios::out );

读写方式打开文件  
fstream rwfile ( "myfile.dat" , ios::in | ios::out );

读写二进制文件  
fstream ioFile;  
ioFile.open( file2, ios::in|ios::out|ios::binary);  
ofstream  ofile ( "a:\\binary" , ios :: binary | ios

![](bbox=[0.745, 0.304, 0.995, 0.554])

![](bbox=[0.745, 0.594, 0.995, 0.745])

![](bbox=[0.717, 0.749, 0.995, 0.926])
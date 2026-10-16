
## 3. Pipes and Filters architecture

Example 6. 如下的Unix命令组成一个管道/过滤器程序，将in.txt文件的包含 “Heroin” 的行进行排序，然后将结果输出到out.txt文件中。

```
cat in.txt | grep “Heroin” | sort > out.txt
```

以上命令行的管道/过滤器结构图如下。

in.txt

Cat

Grep

Sort

out.txt

Grep负责在文件in.txt中搜索包含表达式“cocaine”的所有的行，并且将它们输出到下游管道。

将上游管道来的行进行排序，以后写到out.txt中

## Comparison of batch sequential architecture and Pipes and Filters architecture

## 3. Pipes and Filters architecture

Comparison between batch sequential architecture and pipes-and-filters architecture

- **Similarity: independent processing modules**

In both Batch sequential and pipes and filters architectures, the processing steps are independent of each other, that is

- one filter in pipes and filters architecture doesn’t call any other filters in the system
- one processing step in batch sequential architecture doesn’t call any other processing step in the system

处理过程之间互不调用

## 3. Pipes and Filters architecture

Comparison between batch sequential architecture and pipes-and-filters architecture

### Difference 1 (the way for data processing is different):

- 1. In batch sequential Architecture, each step runs to completion before the next step starts, that is, data is transmitted as a whole between steps
- 2. In pipes and filters architecture, the filters Incrementally transform some of the source data into sink data, that is, the filters do stream to stream transformation

## 3. Pipes and Filters architecture

Comparison between batch sequential architecture and pipes-and-filters architecture

### Difference 2 (data amount is different) :

- 1. In batch sequential Architecture, the amount of data is limited
- 2. In pipes and filters architecture, the amount of data can be unlimited

## 3. Pipes and Filters architecture

### Digital Image Processing

- **Image processing problem**
- **Question:** if you are required to do some image processing to digital pictures (images), and you are given two choices, batch sequential and pipes and filters, which one should you select?
- **Processing steps:**
  - Sharpen
  - FindEdges
  - HighlightEdges
  - ProduceReport

![](img/95717dc23f76db2057b9aa0c49790307_207_0.png)

![](img/95717dc23f76db2057b9aa0c49790307_207_1.png)

Picture before and after image sharpening

## Example Pipe-and-Filter System: Khors—An Image-Processing Workbench

![](img/95717dc23f76db2057b9aa0c49790307_208_0.png)

## Image Processing Workbench (IPW)

- IPW is a UNIX-based image processing system.
- IPW includes several UNIX filter programs which can be pipe-lined together to form complex and powerful image processing algorithms.
- IPW includes a development environment for creating new IPW shell scripts and programs in C.
- IPW often provides the simplest, most powerful and efficient methods for manipulating a wide variety of [remote sensing and image data (why?)](blue).

## 3. Pipes and Filters architecture

- 例7 使用批处理体系结构。设计考虑设计一个图像处理软件。该软件应该有一个用户图形界面。该软件包含一些可以随时添加的过滤器（filters），例如，图像模糊(Blurring)，图像锐化(Sharpening)，图像变亮(Brightening)，发现图像边界(EdgeDetector)，每个过滤器完成一项特定的图像处理功能。一些过滤器被串联在一起，以便完成一些比较复杂的功能。我们该系统，如图6.25。

![](img/95717dc23f76db2057b9aa0c49790307_211_0.png)

顺序批处理体系结构的数字图像处理系统对象逻辑图

顺序批处理软件用户界面图

## 3. Pipes and Filters architecture

- 例8 使用管道-过滤器体系结构设计的数字图像处理系统。设计一个管道-过滤器体系结构的数字图像处理系统。其功能包括用户图形界面，RGBFilter，ThreshHoldFilter，TransFilter，GrayOutFilter分别实现对彩色图像的三色素滤波，阈值滤波、变换滤波与变灰滤波。

![](img/95717dc23f76db2057b9aa0c49790307_213_0.png)

设计逻辑

其中, RGBFilter、ThreshHoldFilter、TransFilter、GrayOutFilter对象利用Pipe对象从上游数据流读入数据，进行各种滤波，并且适时地将所产生的数据写到下游数据流中，设计类图如图6.49所示。

![](img/95717dc23f76db2057b9aa0c49790307_215_0.png)

利用管道-过滤器架构设计的数字图像处理系统用户界面图

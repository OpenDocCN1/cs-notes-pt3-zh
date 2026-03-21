# 约翰霍普金斯大学《GPU编程（并发编程、并行编程、面向企业、CUDA高级库）｜GPU Programming》 p88 27_NPP图像处理代码演示.zh_en -BV1a1421r7vw_p88-

So we're going to go through a really quick walk through of the core。



![](img/bd36fc824af76502dbc9f58381847277_1.png)

![](img/bd36fc824af76502dbc9f58381847277_2.png)

Of the box filter MPP to discuss。The syntax in more tangible way。



![](img/bd36fc824af76502dbc9f58381847277_4.png)

So basically I need a host memory pointer to be the source。



![](img/bd36fc824af76502dbc9f58381847277_6.png)

![](img/bd36fc824af76502dbc9f58381847277_7.png)

And I'm dealing with gray scale， so I need it to be an eight bit unsigned。

 and it only has one channel。

![](img/bd36fc824af76502dbc9f58381847277_9.png)

So that's what's on here I use。

![](img/bd36fc824af76502dbc9f58381847277_11.png)

A ability to load an image using free image， so that is of course loaded into the environment you use。

 I give it a file name which was part of the other part of the program。😔。



![](img/bd36fc824af76502dbc9f58381847277_13.png)

![](img/bd36fc824af76502dbc9f58381847277_14.png)

![](img/bd36fc824af76502dbc9f58381847277_15.png)

And then the pointer， and it loads the data。

![](img/bd36fc824af76502dbc9f58381847277_17.png)

Into that pointer， and it will down sample it will do whatever is needed。

 It'll take that RGP image and make it into a gray scale。 It'll do whatever it needs to do。



![](img/bd36fc824af76502dbc9f58381847277_19.png)

![](img/bd36fc824af76502dbc9f58381847277_20.png)

The next thing is to create。deviceice memory pointer and note the only difference here。 it says MPP。

 whereas up here， it says CPU to' the same number of。



![](img/bd36fc824af76502dbc9f58381847277_22.png)

![](img/bd36fc824af76502dbc9f58381847277_23.png)

Channels in the same number of bits。

![](img/bd36fc824af76502dbc9f58381847277_25.png)

And you pass it， the pointer to host memory and it deals with。



![](img/bd36fc824af76502dbc9f58381847277_27.png)

The malic side of things so you could do it yourself There's some specific things I'm doing here that are part of MPP and specifically the image processing capability that's set up the filter。

 so you need a mask so the filter operates on a kernel that is5 by5 when I say kernel I mean in the classic image processing way。



![](img/bd36fc824af76502dbc9f58381847277_29.png)

![](img/bd36fc824af76502dbc9f58381847277_30.png)

![](img/bd36fc824af76502dbc9f58381847277_31.png)

![](img/bd36fc824af76502dbc9f58381847277_32.png)

![](img/bd36fc824af76502dbc9f58381847277_33.png)

And that's 5 by 5。 And then you have to say what the source size for your image is。

 So you base that on the input size。

![](img/bd36fc824af76502dbc9f58381847277_35.png)

![](img/bd36fc824af76502dbc9f58381847277_36.png)

Or you can do it from the device source you're just getting that with。

 you could hard code this if you wanted。

![](img/bd36fc824af76502dbc9f58381847277_38.png)

![](img/bd36fc824af76502dbc9f58381847277_39.png)

And then if you didn't want the filter to start at the very top left pixel。

 you would give different values， but the X and Y are specified here。



![](img/bd36fc824af76502dbc9f58381847277_41.png)

![](img/bd36fc824af76502dbc9f58381847277_42.png)

Then， you say。What the region of interest is。 So yet again， not only is the source defined。

 but the region of interest。 so you could。

![](img/bd36fc824af76502dbc9f58381847277_44.png)

![](img/bd36fc824af76502dbc9f58381847277_45.png)

Specify a box within the larger image。 the ROI or region of interest cannot be larger than the source image。



![](img/bd36fc824af76502dbc9f58381847277_47.png)

![](img/bd36fc824af76502dbc9f58381847277_48.png)

And then。You have to say where you want the results of the processing to go。

 so you give it a pointer to a different memory location。

 and you give it the size that you've defined here with Os Ri。



![](img/bd36fc824af76502dbc9f58381847277_50.png)

![](img/bd36fc824af76502dbc9f58381847277_51.png)

![](img/bd36fc824af76502dbc9f58381847277_52.png)

The last thing you have to do is you have to give。

![](img/bd36fc824af76502dbc9f58381847277_54.png)

And at a point that's the anchor。 So that means around which all the operations will start。

 So if you give it a window。

![](img/bd36fc824af76502dbc9f58381847277_56.png)

![](img/bd36fc824af76502dbc9f58381847277_57.png)

Of this is the region of interest。 you also have to say， while that's a size。

 now I need to tell you where an X， Y coordinates in the image。

 So if you want it to be done in everything， the combination is you're going to make the anchor。

 the middle pixel both x and Y and make the size of the region of interest。

 the size of the whole image。

![](img/bd36fc824af76502dbc9f58381847277_59.png)

![](img/bd36fc824af76502dbc9f58381847277_60.png)

![](img/bd36fc824af76502dbc9f58381847277_61.png)

![](img/bd36fc824af76502dbc9f58381847277_62.png)

Then do some stuff with checking for errors here。

![](img/bd36fc824af76502dbc9f58381847277_64.png)

And， and you run the MPP I filter box border。😔。

![](img/bd36fc824af76502dbc9f58381847277_66.png)

8ight。Unsigned one channel。😔。

![](img/bd36fc824af76502dbc9f58381847277_68.png)

And only red。In this case。So the box filter works as a box and。Produces a certain effect。



![](img/bd36fc824af76502dbc9f58381847277_70.png)

But because it works in a kernel， you， you want to have the kernel not sort of go off and。

 and be operating on pixels that don't even exist that are around the outside of。



![](img/bd36fc824af76502dbc9f58381847277_72.png)

![](img/bd36fc824af76502dbc9f58381847277_73.png)

The image。😔，So you you add this port and the way to do it so it works on all the pixels is。



![](img/bd36fc824af76502dbc9f58381847277_75.png)

You won't see the change in the border that tends to be unmodified。

 but everywhere else you give it the size of the。

![](img/bd36fc824af76502dbc9f58381847277_77.png)

![](img/bd36fc824af76502dbc9f58381847277_78.png)

。

![](img/bd36fc824af76502dbc9f58381847277_80.png)

Mask， that mask， you give it half of that。 and you， you give that to the border。

 and it knows how to calculate。 It's a lot of words to just say。



![](img/bd36fc824af76502dbc9f58381847277_82.png)

![](img/bd36fc824af76502dbc9f58381847277_83.png)

That if you， you want the effect to not。

![](img/bd36fc824af76502dbc9f58381847277_85.png)

Gives zeros， especially in a gray scale image that can have a very large effect。

 Then you can use this。

![](img/bd36fc824af76502dbc9f58381847277_87.png)

Borer。Type of box filter。

![](img/bd36fc824af76502dbc9f58381847277_89.png)

And then。You once your done that should exist inside this O device。



![](img/bd36fc824af76502dbc9f58381847277_91.png)

TST or destination， you're going to want to create that object based on。



![](img/bd36fc824af76502dbc9f58381847277_93.png)

![](img/bd36fc824af76502dbc9f58381847277_94.png)

The size of， of this， of the original this device。

![](img/bd36fc824af76502dbc9f58381847277_96.png)

And that's creating the memory in the O host。

![](img/bd36fc824af76502dbc9f58381847277_98.png)

DST。😔，Data type。And then you do a copy to。 So there's an underlying capability in on the host side of things to copy to and from。



![](img/bd36fc824af76502dbc9f58381847277_100.png)

![](img/bd36fc824af76502dbc9f58381847277_101.png)

A device。

![](img/bd36fc824af76502dbc9f58381847277_103.png)

And it' memory。 so you give it the data， which is。

![](img/bd36fc824af76502dbc9f58381847277_105.png)

In the the heart of this O device DSST， and then you say the pitch。

 which in again is a capability to say I only want so much of this image。 In our case。

 the pitch is the 0，0 pixel。 so it's the top left。

![](img/bd36fc824af76502dbc9f58381847277_107.png)

![](img/bd36fc824af76502dbc9f58381847277_108.png)

And then you save the image yet again， using some utilities that under the hood， utilize free image。

 and then we print some as says about saving the image。 And lastly。

 we free up the two device pointers。 You don't have to worry about freeing up the host pointers。

 but it is possible。

![](img/bd36fc824af76502dbc9f58381847277_110.png)

![](img/bd36fc824af76502dbc9f58381847277_111.png)

![](img/bd36fc824af76502dbc9f58381847277_112.png)

![](img/bd36fc824af76502dbc9f58381847277_113.png)

That you could define pointers to device memory， not allocate them in something else。

 another kernel or another MPP process would want to use them， and it wouldn't have access to them。



![](img/bd36fc824af76502dbc9f58381847277_115.png)

![](img/bd36fc824af76502dbc9f58381847277_116.png)

![](img/bd36fc824af76502dbc9f58381847277_117.png)
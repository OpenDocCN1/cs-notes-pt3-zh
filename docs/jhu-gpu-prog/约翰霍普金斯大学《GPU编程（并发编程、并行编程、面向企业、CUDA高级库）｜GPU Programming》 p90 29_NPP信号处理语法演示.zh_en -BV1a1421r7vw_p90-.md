# 约翰霍普金斯大学《GPU编程（并发编程、并行编程、面向企业、CUDA高级库）｜GPU Programming》 p90 29_NPP信号处理语法演示.zh_en -BV1a1421r7vw_p90-

![](img/0a38a27738143eac88e8973622dbd6ba_0.png)

So just like with the MPPI module under NPP， we're going to really quickly talk。😔。



![](img/0a38a27738143eac88e8973622dbd6ba_2.png)

About the MPPS syntax and give you a a realistic example。

 Now this is based on something that was found on。

![](img/0a38a27738143eac88e8973622dbd6ba_4.png)

![](img/0a38a27738143eac88e8973622dbd6ba_5.png)

![](img/0a38a27738143eac88e8973622dbd6ba_6.png)

Forums under the developer toolkit for NviDdia， it gives you a good idea of。



![](img/0a38a27738143eac88e8973622dbd6ba_8.png)

Some of the things people are dealing with， specifically they're dealing with this mean filter and an issue that happens with it。



![](img/0a38a27738143eac88e8973622dbd6ba_10.png)

![](img/0a38a27738143eac88e8973622dbd6ba_11.png)

So it still works， it's a slight distortion of the signal。

 but in this case it's a good example to walk through。



![](img/0a38a27738143eac88e8973622dbd6ba_13.png)

So。

![](img/0a38a27738143eac88e8973622dbd6ba_15.png)

Initially what we need to do is we need to have the pointer for the signal。

 in this case it's a 32 bit floating point signal。

![](img/0a38a27738143eac88e8973622dbd6ba_17.png)

![](img/0a38a27738143eac88e8973622dbd6ba_18.png)

We're just going to generate it randomly or in this case， it's actually all ones。And then。



![](img/0a38a27738143eac88e8973622dbd6ba_20.png)

We have that， we this is the host， we need to copy it over onto the device， so we do a kuda malic。



![](img/0a38a27738143eac88e8973622dbd6ba_22.png)

And for that size device memory， and then we do a kaM copy。



![](img/0a38a27738143eac88e8973622dbd6ba_24.png)

![](img/0a38a27738143eac88e8973622dbd6ba_25.png)

So once that's done。In this PFC image device。

![](img/0a38a27738143eac88e8973622dbd6ba_27.png)

It has the floating point integers that it needs。

![](img/0a38a27738143eac88e8973622dbd6ba_29.png)

What you're going to do then is get this does some things where it gets the memory usage for Kuda。



![](img/0a38a27738143eac88e8973622dbd6ba_31.png)

![](img/0a38a27738143eac88e8973622dbd6ba_32.png)

And then it's going to need to create a buffer。And。

There's this NP mean get buffer size and for the 32 bit floating。Complex。



![](img/0a38a27738143eac88e8973622dbd6ba_34.png)

Nummeric value， the length would be the length of the loop here。 so it's the size。

 and then the buffer size is the same。 They're both both the length of the thing you're going through and the buffer are the same。

 and that's just so you always have sufficient。😔。

![](img/0a38a27738143eac88e8973622dbd6ba_36.png)

![](img/0a38a27738143eac88e8973622dbd6ba_37.png)

![](img/0a38a27738143eac88e8973622dbd6ba_38.png)

Memory to do。The mean operation。 and it the buffer also helps with around the edges of the signal。



![](img/0a38a27738143eac88e8973622dbd6ba_40.png)

![](img/0a38a27738143eac88e8973622dbd6ba_41.png)

So now you want to。You're going to get some information about the statistics related to creating that buffer。

 Now that was a host pointer and now you you're going to create a device pointer。😔。



![](img/0a38a27738143eac88e8973622dbd6ba_43.png)

![](img/0a38a27738143eac88e8973622dbd6ba_44.png)

And that's why you do the k amount copying from the。



![](img/0a38a27738143eac88e8973622dbd6ba_46.png)

AHost pointer for the buffer to the device pointer。



![](img/0a38a27738143eac88e8973622dbd6ba_48.png)

So this this sort of like parallel， you're creating the actual signal and the buffer。



![](img/0a38a27738143eac88e8973622dbd6ba_50.png)

And then the next thing you're going to do is actually perform the mean。

 So you want to have that same size。

![](img/0a38a27738143eac88e8973622dbd6ba_52.png)

嗯。Primitive 32 B floating。

![](img/0a38a27738143eac88e8973622dbd6ba_54.png)

Numbers， it's a complex object so it has some。The actual way you specify it can be with。



![](img/0a38a27738143eac88e8973622dbd6ba_56.png)

A whole number， a comma， and then a number that represents。



![](img/0a38a27738143eac88e8973622dbd6ba_58.png)

The level of digits。 So it's sort of like a floating point， but gives you more complexity。



![](img/0a38a27738143eac88e8973622dbd6ba_60.png)

![](img/0a38a27738143eac88e8973622dbd6ba_61.png)

The number of ditits it can represent is larger。So this is important because you might have a mean that goes many significant digits below the whole digit。



![](img/0a38a27738143eac88e8973622dbd6ba_63.png)

So you give this MP mean。

![](img/0a38a27738143eac88e8973622dbd6ba_65.png)

Li。😔。

![](img/0a38a27738143eac88e8973622dbd6ba_67.png)

Dvicice pointer for the signal， the length of it。

![](img/0a38a27738143eac88e8973622dbd6ba_69.png)

The pointer to the output， which is this Fc mean， and then the buffer that you've created。



![](img/0a38a27738143eac88e8973622dbd6ba_71.png)

You let that go and just to make sure you don't print out nothing。

 it's always good to add that coed device synchronize to ensure that the operation is completed。

 it may take a while based on the amount of data。

![](img/0a38a27738143eac88e8973622dbd6ba_73.png)

![](img/0a38a27738143eac88e8973622dbd6ba_74.png)

![](img/0a38a27738143eac88e8973622dbd6ba_75.png)

And then there's some stuff to see what the available and total memory is on the card。



![](img/0a38a27738143eac88e8973622dbd6ba_77.png)

And then。you could printnounce some stuff about whether it failed or not。

 in this case it's pretty negative， but you would then output that either to some visualization capability or to a file。



![](img/0a38a27738143eac88e8973622dbd6ba_79.png)

![](img/0a38a27738143eac88e8973622dbd6ba_80.png)

![](img/0a38a27738143eac88e8973622dbd6ba_81.png)

You want to delete the pointers to the signals on the host。😔。



![](img/0a38a27738143eac88e8973622dbd6ba_83.png)

Then you have free up memory for the the device for the signal and the device memory for the buffer。

 and then you can get。

![](img/0a38a27738143eac88e8973622dbd6ba_85.png)

![](img/0a38a27738143eac88e8973622dbd6ba_86.png)

The information in Ken， and again， if it's the only thing that's running on the GPU。

 this would actually end up being the same value for the frame in the total。



![](img/0a38a27738143eac88e8973622dbd6ba_88.png)

![](img/0a38a27738143eac88e8973622dbd6ba_89.png)

Thank you。😔。

![](img/0a38a27738143eac88e8973622dbd6ba_91.png)
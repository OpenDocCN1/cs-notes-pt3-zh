# LLVM入门教程-•-中英-p10-P10-Writing-a-LLVM-based-tool--BV1HtRUYnEji_p10-

Hello， everyone。 I'm L Soides from UFMG and in the previousors。We saw the basics of relevant passes。

 we saw how to write a very simple analysis， and then how to implement a transformation pass that consumes this analysis。

And this is pretty much what you needed to start working with A them to start。

Wrt in your own analysis your optimizations。But there are other features that you can explore。

 and one of them is the command line。うん。APpiI that you can use to write your own tool based on all of M。

 So this is basically what we're going to do in this video。 we're going to write a tool。



![](img/595b2c6f4e36bd394b869fd8f4c43a38_1.png)

That using this API that will apply where。Or to submission pass。And we're going to。

 we're going to use these tool instead of O P T。 We transform the。Example that we have。



![](img/595b2c6f4e36bd394b869fd8f4c43a38_3.png)

So first a briefcap about our analysis and we have a list of instructions of ad additions。

And some of them only uses。Con opera and our analysis collect this sort of instructions。

 So in this case， in this example， the first two additions only use concept opera。



![](img/595b2c6f4e36bd394b869fd8f4c43a38_5.png)

So the result of analysis would be at least with these two instructions。

And then we use this this list。In our transformation path to evaluate these additions at compile time and replace。

Then by their final value。

![](img/595b2c6f4e36bd394b869fd8f4c43a38_7.png)

And this is the structure of our product at And right now， we have a mamic file。

 We have included folder for our headers。 We have a lip folder。

For source files and a beautiful folder for visual generated files。



![](img/595b2c6f4e36bd394b869fd8f4c43a38_9.png)

And re and create a new folder to to store the source fileifier2。



![](img/595b2c6f4e36bd394b869fd8f4c43a38_11.png)

As well as another Sic file。And let's start with the se file which is。Quite simple。 And first。

 we add our executable。 In this case， we call it as add cost， and we list the source files。



![](img/595b2c6f4e36bd394b869fd8f4c43a38_13.png)

That we need for to work。Then， then we link our executable with all of them libraries。

 of them passes。

![](img/595b2c6f4e36bd394b869fd8f4c43a38_15.png)

And finally， we our include directory so we can use our passes。And that the。



![](img/595b2c6f4e36bd394b869fd8f4c43a38_17.png)

A do bB file。

![](img/595b2c6f4e36bd394b869fd8f4c43a38_19.png)

And now the actual implementation， we first start by creating a category for our options or command line options。

And in this case， we're going to have only two options。 The first one is the input file。

 which is required。

![](img/595b2c6f4e36bd394b869fd8f4c43a38_21.png)

And the second one is the output file page in case I made it optional and I have a default value。

 which is out do L。O to dot L。And after that， we move。To the main function。

And the first thing here is to hide unrelated options。 We only want。

The options we defined to be shown to appear to the users。And then we parse command line options。

And we try to， to pass the input file。And if something went wrong。We print there， and return。

And otherwise， we now have a valid input that we can use。

So the first thing is to is to create a new instance of our transformation pass and a new instance of a function pass manager。

 here we're going to sort of do what。Is implemented in no beauty。



![](img/595b2c6f4e36bd394b869fd8f4c43a38_23.png)

And。So we create our functional pass manager， then we add our transformation pass to it。

Then we create a function analysis manager and register our analysis， so our best。

We'll be able to use it later on。And then we create a pest builder to register our functional analysis。

To here you through the L default analysis， as well as our analysis。And finally。

 we traverse all the functions in the module。And run。Our press， apply and apply our press into them。



![](img/595b2c6f4e36bd394b869fd8f4c43a38_25.png)

![](img/595b2c6f4e36bd394b869fd8f4c43a38_26.png)

And that's basically。 Then after that， we。Wry to write the transformment cool into the output file。



![](img/595b2c6f4e36bd394b869fd8f4c43a38_28.png)

And if everything went。Well， now we have。transform file。We have the constant additions eliminated。So。

 that's pretty much it。呃。So let's build this project here， I'm using A of M version 11。

 the previous videos I was using A M12 compiled from source。

 but I had some problems and I couldn't fix it。

![](img/595b2c6f4e36bd394b869fd8f4c43a38_30.png)

And so I just moved back and it' working in 1111。And then we generate thebu files and we move to the But folder to compile our project。



![](img/595b2c6f4e36bd394b869fd8f4c43a38_32.png)

And now inside the build folder， we have a beam folder we are executable and we can use it to transform our example。

And so on the left， we have the original file on the right， we have。The the transform code。

We have the true first editions。We replace the two first editions。With their result。



![](img/595b2c6f4e36bd394b869fd8f4c43a38_34.png)

And that's basically it。Thank you， everyone。 And if you have any questions。

 you can leave in the comments。

![](img/595b2c6f4e36bd394b869fd8f4c43a38_36.png)
# 约翰霍普金斯大学《入侵检测｜Intrusion Detection》中英字幕 - P55：5_支持向量机算法.zh_en - GPT中英字幕课程资源 - BV1sGu1z5E2J

![](img/904523f8d18e44052056295a4234e4b6_0.png)

Welcome to the very last lecture in the Introuction to Mach learninging module where we will talk about support vector machines and give you a brief introduction to what this particular technique is。



![](img/904523f8d18e44052056295a4234e4b6_2.png)

![](img/904523f8d18e44052056295a4234e4b6_3.png)

Let's start with a very basic binary classification problem here what we want to do is find a line that separates our green squares from our red circles and in this case we have something that' is literally separable so we know all we need is a line between the two。



![](img/904523f8d18e44052056295a4234e4b6_5.png)

![](img/904523f8d18e44052056295a4234e4b6_6.png)

![](img/904523f8d18e44052056295a4234e4b6_7.png)

Now， the question becomes， where should we draw that line。 So， for example。

 we could have something that goes roughly like this。 Sorry。

 I'm not very good at drawing straight lines。

![](img/904523f8d18e44052056295a4234e4b6_9.png)

![](img/904523f8d18e44052056295a4234e4b6_10.png)

But that will separate our two classes。 but another possible line might be more like this。



![](img/904523f8d18e44052056295a4234e4b6_12.png)

Or yet again， another possible line might give more through the middle between the two。



![](img/904523f8d18e44052056295a4234e4b6_14.png)

So the question becomes， really， what is the best separator that we could have between these two classes？



![](img/904523f8d18e44052056295a4234e4b6_16.png)

Well， the way the support vector machine works is it wants to try to find the line between the two that provides the best separation and the goal for that is really to have the best generalization if you have a line。

 so for example taking this blue line， it's too close to the red circles and so if you have another red circle that happens to be say here。



![](img/904523f8d18e44052056295a4234e4b6_18.png)

![](img/904523f8d18e44052056295a4234e4b6_19.png)

That should be considered a red circle because of how close it is to the cluster of other red circles。

 but if your division was this blue line， it would be classified as incorrectly as a green square。



![](img/904523f8d18e44052056295a4234e4b6_21.png)

![](img/904523f8d18e44052056295a4234e4b6_22.png)

And so you want to find the line that actually maximizes the space such that you know you'll get the best possible classification。



![](img/904523f8d18e44052056295a4234e4b6_24.png)

![](img/904523f8d18e44052056295a4234e4b6_25.png)

So a support vector machine is called what's called a large margin linear classifier。

 it tries to give you the largest margin possible between the two sets of classifications。



![](img/904523f8d18e44052056295a4234e4b6_27.png)

![](img/904523f8d18e44052056295a4234e4b6_28.png)

And so here we see the same thing but with better drawings than what I've been able to do。

 and what you're trying to do is take your margin M here and make that as wide as possible。

 and so this line B1 really is the line that you want for having your margin and not this line B2 because this gives you the widest space between the two classes。



![](img/904523f8d18e44052056295a4234e4b6_30.png)

![](img/904523f8d18e44052056295a4234e4b6_31.png)

![](img/904523f8d18e44052056295a4234e4b6_32.png)

![](img/904523f8d18e44052056295a4234e4b6_33.png)

So a brief introduction to what's happening here mathematically。

 what we're doing is we have a function and it's going to say that everything that lives above the one line that defines your B11 line。

Or your margin here。

![](img/904523f8d18e44052056295a4234e4b6_35.png)

Everything in that classification is going to be given a value of one，1，1， one， one， one。



![](img/904523f8d18e44052056295a4234e4b6_37.png)

1 M1。Everything that goes below the line B12。It's going to be classified as a -1，-1，-1。So。

 all of these。Or minus-1。And that's how the classification will work when you run something through the function。

 it's going to see basically is it below the one line or above the other and then say it's either one or minus one because it's a binary classification。



![](img/904523f8d18e44052056295a4234e4b6_39.png)

![](img/904523f8d18e44052056295a4234e4b6_40.png)

The actual equation for the line is your weight vector multiplied by your feature vector for point for your x。

 your input， plus some bias term， and if it's equal to plus1， then well。

 if it's equal to plus1 it defines that particular margin line here。

 same thing but if it's equal to a minus1， it defines this margin line here and if it's equal to zero is the point in between。



![](img/904523f8d18e44052056295a4234e4b6_42.png)

![](img/904523f8d18e44052056295a4234e4b6_43.png)

The widthits of the margin through some beauty of mathematics actually ends up having a very precise definition to maximize your margin。

 which is to divide it by the norm of your weight vector。

 so there's a lot of mathematics go into exactly how to define this and how to look at it。



![](img/904523f8d18e44052056295a4234e4b6_45.png)

![](img/904523f8d18e44052056295a4234e4b6_46.png)

![](img/904523f8d18e44052056295a4234e4b6_47.png)

So the question then becomes， how do you determine really where these margins are？



![](img/904523f8d18e44052056295a4234e4b6_49.png)

And also， what is a support vector？

![](img/904523f8d18e44052056295a4234e4b6_51.png)

Well， what's actually happening is this screen square here and。

This red circle here are on your margin line。

![](img/904523f8d18e44052056295a4234e4b6_53.png)

And so they actually don't have the value， I not lying here， they don't have the value minus1 and1。

 that they're going to have some other value。

![](img/904523f8d18e44052056295a4234e4b6_55.png)

![](img/904523f8d18e44052056295a4234e4b6_56.png)

And these are called your support factors， they're the ones that help define where your margin is and again。

 through the beauty of mathematics， you get to use these to determine where your point lies and so if you end up getting a point that is。

 say you end up with something out here。

![](img/904523f8d18e44052056295a4234e4b6_58.png)

Because it's to that side of your support vector， it gets defined as one and therefore classified as being a red circle。



![](img/904523f8d18e44052056295a4234e4b6_60.png)

![](img/904523f8d18e44052056295a4234e4b6_61.png)

Similarly， on the other side with the green squares。

 it would be classified as a minus1 and therefore it's a green square。

So what happens if you happen to get a green square。Here。



![](img/904523f8d18e44052056295a4234e4b6_63.png)

Well， that will actually be defined as a green square because your actual margin is this line here and so it's still below the margin and then will therefore be classified as a minus1。

 but it is in that that level of error that you've been able to allow yourself again。

 this is why you're maximizing your margin。 So you're most likely if you have something that's。



![](img/904523f8d18e44052056295a4234e4b6_65.png)

![](img/904523f8d18e44052056295a4234e4b6_66.png)

Not exactly within the cluster to still categorize it correctly。



![](img/904523f8d18e44052056295a4234e4b6_68.png)

![](img/904523f8d18e44052056295a4234e4b6_69.png)

So now what happens if you have a green square and it happens to be there。



![](img/904523f8d18e44052056295a4234e4b6_71.png)

Well， what will happen in this case is it will be incorrectly classified as a red circle。

 and that's just because of where the margin is and how we've actually separated the two classes。

 that one is much closer to all the red circles and it therefore is going to be classified as being a red circle。



![](img/904523f8d18e44052056295a4234e4b6_73.png)

![](img/904523f8d18e44052056295a4234e4b6_74.png)

![](img/904523f8d18e44052056295a4234e4b6_75.png)

So that was talking about it in terms of then classifying something that using margins that' already been determined。

 what happens in a case like this where you have these green squares that are over on the red circle side and conversely these red circles on the green square side and you're still trying to train your algorithm。

 is there any way to do this because your' classes here。

 there's small enough error that you can still say there's a linear classification between them with some error。



![](img/904523f8d18e44052056295a4234e4b6_77.png)

![](img/904523f8d18e44052056295a4234e4b6_78.png)

![](img/904523f8d18e44052056295a4234e4b6_79.png)

![](img/904523f8d18e44052056295a4234e4b6_80.png)

![](img/904523f8d18e44052056295a4234e4b6_81.png)

And it turns out that mathematically you can allow this to happen。

 You can have something called soft margins， which is represented by variable C and allow us with some amount of error in your equation。

 so when you see the equation that we had above with your weight vector multiplied by your x vector plus your bias term。

 you've also taken into account some amount of error with that term as well。

 and so it is possible to still find this linear classifier。



![](img/904523f8d18e44052056295a4234e4b6_83.png)

![](img/904523f8d18e44052056295a4234e4b6_84.png)

![](img/904523f8d18e44052056295a4234e4b6_85.png)

![](img/904523f8d18e44052056295a4234e4b6_86.png)

![](img/904523f8d18e44052056295a4234e4b6_87.png)

![](img/904523f8d18e44052056295a4234e4b6_88.png)

This dividing line， even when you have errors， what would I call errors in the input or non perfect input。



![](img/904523f8d18e44052056295a4234e4b6_90.png)

![](img/904523f8d18e44052056295a4234e4b6_91.png)

At this point， I'm going to point out that there are other approaches to finding this boundary between two classes。

 for example。

![](img/904523f8d18e44052056295a4234e4b6_93.png)

When we looked at neural networks in the very first lecture of this module。

 that was another way of finding a dividing line between your two classes。

 the approach that neural network takes or perceptron trait takes is to minimize at least square error using a gradient descent method。



![](img/904523f8d18e44052056295a4234e4b6_95.png)

![](img/904523f8d18e44052056295a4234e4b6_96.png)

![](img/904523f8d18e44052056295a4234e4b6_97.png)

Conversely， what a support vector machine does is it maximizes the margin so that you have the largest amount of space possible between your two classes and so that's really the difference in the approaches is that。



![](img/904523f8d18e44052056295a4234e4b6_99.png)

![](img/904523f8d18e44052056295a4234e4b6_100.png)

![](img/904523f8d18e44052056295a4234e4b6_101.png)

The one is saying， all right， where can I draw the line so that I have the least error in my separations？

The other one is saying， okay， where can I draw the line such that I have the greatest space between my two categories？



![](img/904523f8d18e44052056295a4234e4b6_103.png)

![](img/904523f8d18e44052056295a4234e4b6_104.png)

And again， I'm going to point out here you can see where your support vector are。

 so you have this red square here。

![](img/904523f8d18e44052056295a4234e4b6_106.png)

Right along them at the margin line and this blue circle here， forming your support vectors。



![](img/904523f8d18e44052056295a4234e4b6_108.png)

And so really forming the basis of what your calculation is。



![](img/904523f8d18e44052056295a4234e4b6_110.png)

So these have all been examples so far of a binary classification with a linear separator。

 what happens and an example that had some error as well。

 but what happens if you have two classes that are actually not linearly separable？



![](img/904523f8d18e44052056295a4234e4b6_112.png)

![](img/904523f8d18e44052056295a4234e4b6_113.png)

![](img/904523f8d18e44052056295a4234e4b6_114.png)

So here is an example of a space that is not linearly separable。

 so what we really want some way to have a curved boundary。



![](img/904523f8d18e44052056295a4234e4b6_116.png)

![](img/904523f8d18e44052056295a4234e4b6_117.png)

Nor to split these two spaces， so how do you do that？Well， in this case。

 we use something called a kernel trick。which I'll explain in a minute。



![](img/904523f8d18e44052056295a4234e4b6_119.png)

But essentially what it does is it creates additional feature spaces。



![](img/904523f8d18e44052056295a4234e4b6_121.png)

And tries to separate the data so that it does become linearly separable。

 and then you can create a hyperplane that separates your two sets of data。



![](img/904523f8d18e44052056295a4234e4b6_123.png)

So we call this a linear separation inssori in two dimensional data。



![](img/904523f8d18e44052056295a4234e4b6_125.png)

Once we go up to three dimensional data it becomes a plane that separates our two spaces。

 once we go beyond three dimensions， it becomes it's called a hyperplane。

 but the same basic idea you have something that linearly separates your two spaces。

 and so by taking this two dimensional space and breaking it out into a larger feature space。

 we're able to get that linear separation。

![](img/904523f8d18e44052056295a4234e4b6_127.png)

![](img/904523f8d18e44052056295a4234e4b6_128.png)

So what is a kernel function then and how does it work，Essentially。

 what a kernel function does is it takes your n dimensional space and maps it into a higher dimensional feature space。

 and one of the very。

![](img/904523f8d18e44052056295a4234e4b6_130.png)

![](img/904523f8d18e44052056295a4234e4b6_131.png)

![](img/904523f8d18e44052056295a4234e4b6_132.png)

Commonly used kernel functions， maps a pair of data points onto their inner product。

 And so essentially， it works very similar to a distance function。

 But what you want to do is take every。

![](img/904523f8d18e44052056295a4234e4b6_134.png)

![](img/904523f8d18e44052056295a4234e4b6_135.png)

Every pair of data points and then use do an inner product so that you map into a larger feature space。



![](img/904523f8d18e44052056295a4234e4b6_137.png)

What this effectively does is twofold one by manipulating your points in the feature space。

 essentially what you're doing is you're either stretching some areas of the space or you're compressing some of the other areas and by doing this and changing essentially changing your distance a little bit。

 you are creating a separation between the two classes of data points so that you can put a hyperplane there and actually find your separate how you separate the data。



![](img/904523f8d18e44052056295a4234e4b6_139.png)

![](img/904523f8d18e44052056295a4234e4b6_140.png)

![](img/904523f8d18e44052056295a4234e4b6_141.png)

![](img/904523f8d18e44052056295a4234e4b6_142.png)

嗯。

![](img/904523f8d18e44052056295a4234e4b6_144.png)

The second point to note on this is that this works not on the features that you have。

 but actually on the data points that you have， and so if you start with 10 points。

 your feature space actually becomes 100 dimensions because you're starting with 10 inputs as opposed to starting and necessarily with 10 features。



![](img/904523f8d18e44052056295a4234e4b6_146.png)

![](img/904523f8d18e44052056295a4234e4b6_147.png)

This is an important distinction because what it means is that this increase scales with the number of inputs that you have in your training set。

 as opposed with the number of features that you have。



![](img/904523f8d18e44052056295a4234e4b6_149.png)

![](img/904523f8d18e44052056295a4234e4b6_150.png)

So if you have some space that has a thousand0 features， but only 10 samples。

 you can increase your feature space based on the number of samples and based on only 10 as opposed to doing that increase based on the number of features to say 1000。



![](img/904523f8d18e44052056295a4234e4b6_152.png)

![](img/904523f8d18e44052056295a4234e4b6_153.png)

![](img/904523f8d18e44052056295a4234e4b6_154.png)

And therefore， that computational complexity is reduced considerably。

 and so you have a faster algorithm。By coming up with a calculation of a hyperplane in this higher dimensional space。

 what actually effectively happens is that you've ended up creating a curved line in your lower dimensional space。

 so in this case in our two dimensional space， we have this curved line here。



![](img/904523f8d18e44052056295a4234e4b6_156.png)

![](img/904523f8d18e44052056295a4234e4b6_157.png)

![](img/904523f8d18e44052056295a4234e4b6_158.png)

![](img/904523f8d18e44052056295a4234e4b6_159.png)

That actually separates properly the two classes of data that we have because we've used this kernel trick to try to split or split out。



![](img/904523f8d18e44052056295a4234e4b6_161.png)

And separate better the two binary classifications。



![](img/904523f8d18e44052056295a4234e4b6_163.png)

And create more distance between them so that we could put a linear separator there。



![](img/904523f8d18e44052056295a4234e4b6_165.png)

There are different kernel functions that you can use。

 but this is essentially how all of them work is by creating this space between the two classes。



![](img/904523f8d18e44052056295a4234e4b6_167.png)

![](img/904523f8d18e44052056295a4234e4b6_168.png)

I'm going to take a step back at this point and talk about something called overfitting and generalization。



![](img/904523f8d18e44052056295a4234e4b6_170.png)

So in the case of support vector machines， you want to make sure you avoid something called overfitting so that you have a result that generalizes well in this case。

 if we look at this first graph what we have here。

![](img/904523f8d18e44052056295a4234e4b6_172.png)

![](img/904523f8d18e44052056295a4234e4b6_173.png)

![](img/904523f8d18e44052056295a4234e4b6_174.png)

Is a perfect fit of a linear line through a set of data points。



![](img/904523f8d18e44052056295a4234e4b6_176.png)

Now， assume looking at the second graph that we have the blue dots as our training data。

We have two possible algorithms， we have one algorithm that provides this straight line through the data algorithm 2。

 or we have algorithm one that actually perfectly represents every single point in the training data。



![](img/904523f8d18e44052056295a4234e4b6_178.png)

The question then becomes which of these two algorithms is the one that actually best represents the class of data that we're trying to model。



![](img/904523f8d18e44052056295a4234e4b6_180.png)

And the answer is algorithm too， even though it's not perfectly representative of every point in the training data。

 what often happens is something called overfitting。 What that means is that。



![](img/904523f8d18e44052056295a4234e4b6_182.png)

![](img/904523f8d18e44052056295a4234e4b6_183.png)

You've actually developed your algorithm or your model that to fit your training data perfectly。

 and because of that， it's overfitted， it represents the training data。

 but does not generalize necessarily to very well to onseen data。



![](img/904523f8d18e44052056295a4234e4b6_185.png)

![](img/904523f8d18e44052056295a4234e4b6_186.png)

Or new data， right you really want this algorithm too that doesn't represent the training data as well。

 but it's more generalizable， meaning it fits all of the onseen data much better。

 And so the model itself is actually better。

![](img/904523f8d18e44052056295a4234e4b6_188.png)

Overfitting and generalization are issues that you see not just in support vector machines。

 but in other types of machine learning as well， so neural networks， for example。

 have very similar issues。

![](img/904523f8d18e44052056295a4234e4b6_190.png)

The in the case of support vector machines， there are things like different paradigms such as a loss plus penalty paradigm that help ensure that you avoid overfitting and so there are approaches to try to minimize that this might happen。

 but it's something to be aware of， not just again for support vector machines but in general when training algorithms that。



![](img/904523f8d18e44052056295a4234e4b6_192.png)

![](img/904523f8d18e44052056295a4234e4b6_193.png)

These are problems that you can run into。So I'm going to leave you then with one last question about support vector machines we've talked about having a binary classification。

 we have two classes of data。

![](img/904523f8d18e44052056295a4234e4b6_195.png)

The question becomes， can you support， can you represent a model or develop a model if you have only one glass of data？



![](img/904523f8d18e44052056295a4234e4b6_197.png)

And can you represent a model if it has multiple classes of data。

 and the answer in both cases is yes， and I'm not going to go into details on it。

 but it is possible to have what's called a one class SVM that trains on just one class of data and essentially becomes an anomaly detector。

 anything that's not part of that class is outside of that class。



![](img/904523f8d18e44052056295a4234e4b6_199.png)

![](img/904523f8d18e44052056295a4234e4b6_200.png)

And you can have multiple a multiclass detector as well。

 and there are different approaches to doing multiclass detectors。



![](img/904523f8d18e44052056295a4234e4b6_202.png)

One of which is to take a number of different。

![](img/904523f8d18e44052056295a4234e4b6_204.png)

One plus everyone else detectors and combine those。

 another is to use support trees so you're bringing in some other machine learning method to help support your support vector method there are different ways of doing these multiclass detectors。

 but it is possible to do a multiclass detector。

![](img/904523f8d18e44052056295a4234e4b6_206.png)

![](img/904523f8d18e44052056295a4234e4b6_207.png)

And with that， I'm going to end the section on support vector machines and talk to you in the next module when now we have this basis of some of the different algorithms available。

 talk about how it is that we can actually use these algorithms for intrusion detection。



![](img/904523f8d18e44052056295a4234e4b6_209.png)

![](img/904523f8d18e44052056295a4234e4b6_210.png)

![](img/904523f8d18e44052056295a4234e4b6_211.png)
# 约翰霍普金斯大学《入侵检测｜Intrusion Detection》中英字幕 - P54：4_聚类分析技术.zh_en - GPT中英字幕课程资源 - BV1sGu1z5E2J

![](img/40d99e508d30145a9e7e167a66bcc875_0.png)

Welcome to Module 11 C， where we will be talking about clustering algorithms。



![](img/40d99e508d30145a9e7e167a66bcc875_2.png)

There are several different types of clustering algorithms in this module I am going to focus on describing the K means clustering algorithm。

 but want you to recognize that there are other types of clustering such as EM clustering。

 DB scan which stands for density-based spatial clustering of applications with noise。

 graph models and Gaussian mixture models among other types of clustering。



![](img/40d99e508d30145a9e7e167a66bcc875_4.png)

In this module， I am also going to talk about K nearest neighbor and what the difference is between that and K means clustering so that you don't mix those two up。

 seeing that they sound similar， but they actually are very， very different in terms of what they do。



![](img/40d99e508d30145a9e7e167a66bcc875_6.png)

So moving on， let's take a look at Ka means's clustering。



![](img/40d99e508d30145a9e7e167a66bcc875_8.png)

Formerally， we can describe the problem for K means clustering as being given a set x of endpoint in a d dimensional space and an integer K。

 group the points into K clusters， C is equal to the set of C1 up through CK。

 such that we have this particular cost function which we are minimizing。

Where lowercase C subs the centroid of the points rather in cluster capital C subi。

So essentially what we're doing is we're taking a large number of points。X， that would be your set X。

 and there are Mpoints in that space。

![](img/40d99e508d30145a9e7e167a66bcc875_10.png)

And it's a D dimensional space， so for example， two dimensions will be easy to visualize and we'll look at that next。



![](img/40d99e508d30145a9e7e167a66bcc875_12.png)

What you want to do is select some k。 So you assume that given this set of points that there might be three different clusters in there。

 for example， so you set k equal to three。 what you're trying to do then is fine。



![](img/40d99e508d30145a9e7e167a66bcc875_14.png)

Three clusters， such that you've minimized the distance between the centroid and every point within those clusters。

What might make more sense is to look at this graphically， which is what we'll do next。



![](img/40d99e508d30145a9e7e167a66bcc875_16.png)

![](img/40d99e508d30145a9e7e167a66bcc875_17.png)

So here is an example of how the algorithm itself looks。

You have an initial data set which consists of， in this case， 12 different points， so all of these。



![](img/40d99e508d30145a9e7e167a66bcc875_19.png)

From there you set k equal to 2， so what you're doing is saying I want to break this set into two different clusters the question then becomes what are the two clusters that you would have？

What you do is you first， you arbitrarily assign all the different points to one of those two clusters。



![](img/40d99e508d30145a9e7e167a66bcc875_21.png)

In this case， we're representing the two clusters as red plus signs and black dots。



![](img/40d99e508d30145a9e7e167a66bcc875_23.png)

You then calculate the centroid for what you've defined for your two clusters。

 and you can see that defined here， one centroid and appear for the other centroid。

Now that you've assigned these centroids based on what you've seen so far。

 you look at all of these points again and reassign those points to the centroid that's closest to them。

 and so you'll see for example this point here， which is closest to this centroid here。

 gets reassigned being a dot rather than a red plus。Now that you have a new cluster。

 you update the cluster centroids so that they are in new positions。

And then you keep looping back through。Once you've updated your cluster centroids。

 you go through and recalculate where are the objects in relation to those centroids and then update those objects and then update the centroid and keep going until you find no change。

 that is all of the points have been assigned to the centroid closest to them and there is no change in where the centroids are located。



![](img/40d99e508d30145a9e7e167a66bcc875_25.png)

![](img/40d99e508d30145a9e7e167a66bcc875_26.png)

![](img/40d99e508d30145a9e7e167a66bcc875_27.png)

![](img/40d99e508d30145a9e7e167a66bcc875_28.png)

Let's look at another example of how this might work。

Here you have a number of circles and they've been assigned either through red or yellow。



![](img/40d99e508d30145a9e7e167a66bcc875_30.png)

You've randomly assigned them and now you calculate where the centroid is。



![](img/40d99e508d30145a9e7e167a66bcc875_32.png)

![](img/40d99e508d30145a9e7e167a66bcc875_33.png)

Originally， you have a centroid that has been put in some position and you're going to move it to its new position。

 So for example， you have the centroid here for red and that gets moved over to this new location based on the location of all of the different dots that are associated with。



![](img/40d99e508d30145a9e7e167a66bcc875_35.png)

![](img/40d99e508d30145a9e7e167a66bcc875_36.png)

Being read with that particular cluster。Similarly， you originally had a centroid up here for the yellow that gets moved down to here based on where all of the points that are assigned to the yellow cluster are so that you've minimized or you found the center for all of those points。

 and essentially minimized your distance。

![](img/40d99e508d30145a9e7e167a66bcc875_38.png)

![](img/40d99e508d30145a9e7e167a66bcc875_39.png)

![](img/40d99e508d30145a9e7e167a66bcc875_40.png)

![](img/40d99e508d30145a9e7e167a66bcc875_41.png)

You then go through and recalculate what points belong to which centroid？



![](img/40d99e508d30145a9e7e167a66bcc875_43.png)

So going over to the second one over here。

![](img/40d99e508d30145a9e7e167a66bcc875_45.png)

What we'll see is that some points have been reassigned to be red instead of yellow， so for example。

 this point and this point were yellow previously and are now red based on the new centroid。



![](img/40d99e508d30145a9e7e167a66bcc875_47.png)

![](img/40d99e508d30145a9e7e167a66bcc875_48.png)

Once you've recalculated all of those points， you then take the centroid here and recalculate where it should be。

 so it's going to move to that location。

![](img/40d99e508d30145a9e7e167a66bcc875_50.png)

You then go down to the next one and redo the same process and you keep doing that until you've defined your clusters and there is no more change in either what is in the cluster or where the centroid itself is located。

 and at that point you have actually finalized what your clusters are。



![](img/40d99e508d30145a9e7e167a66bcc875_52.png)

![](img/40d99e508d30145a9e7e167a66bcc875_53.png)

![](img/40d99e508d30145a9e7e167a66bcc875_54.png)

That was looking at the simple case where we had two clusters。



![](img/40d99e508d30145a9e7e167a66bcc875_56.png)

There can be more than two clusters you could set your k to three for example。

 but the algorithm itself remains the same in this case you have three different centroids that you're dealing with and you keep reassigning your different points within your space to the centroids that are closest to it and then moving the centroids based on what cluster it's in until you have a stable system so in this case you can see that we have three different clusters that we've started with。



![](img/40d99e508d30145a9e7e167a66bcc875_58.png)

![](img/40d99e508d30145a9e7e167a66bcc875_59.png)

![](img/40d99e508d30145a9e7e167a66bcc875_60.png)

![](img/40d99e508d30145a9e7e167a66bcc875_61.png)

![](img/40d99e508d30145a9e7e167a66bcc875_62.png)

![](img/40d99e508d30145a9e7e167a66bcc875_63.png)

And you can see the ending point where we have three different clusters that are quite different from the original。



![](img/40d99e508d30145a9e7e167a66bcc875_65.png)

Based on what we expect we or in of this particular cluster。

 based on the distance between the centroid and each of those different points。



![](img/40d99e508d30145a9e7e167a66bcc875_67.png)

![](img/40d99e508d30145a9e7e167a66bcc875_68.png)

But the examples you've seen so far are actually pretty simple。

 what happens if you have a shape like this and you're trying to do this kind of a K means clustering？



![](img/40d99e508d30145a9e7e167a66bcc875_70.png)

![](img/40d99e508d30145a9e7e167a66bcc875_71.png)

So for example， say you originally pick a centroid from over here and another over here。



![](img/40d99e508d30145a9e7e167a66bcc875_73.png)

If you're then looking for what cluster or what points are closest to it。

 you're probably going to end up with something。

![](img/40d99e508d30145a9e7e167a66bcc875_75.png)

Kind of like this and kind of like。

![](img/40d99e508d30145a9e7e167a66bcc875_77.png)

Yes。So you'll have some space maybe around here that's dividing the two sets。



![](img/40d99e508d30145a9e7e167a66bcc875_79.png)

![](img/40d99e508d30145a9e7e167a66bcc875_80.png)

Obviously， that's not what we want we want to have。

This be one particular cluster and this be another cluster。



![](img/40d99e508d30145a9e7e167a66bcc875_82.png)

![](img/40d99e508d30145a9e7e167a66bcc875_83.png)

So is there any way we can do that， well， yes， but not with K means clustering， the way it it works。

 it's just not going to be able to define that kind of clustering pattern。

 it's more built for your clusters that are more divided and more separated in space than these two are。



![](img/40d99e508d30145a9e7e167a66bcc875_85.png)

![](img/40d99e508d30145a9e7e167a66bcc875_86.png)

嗯。There is another type of clustering that was mentioned before EM clustering does that work Well EM clustering actually takes into a account a bit more information than just distance from the centroid such as items like variants。

 however， what it provides is then the ability to put a shape of an ellipse essentially around what you're looking at rather than a circle。



![](img/40d99e508d30145a9e7e167a66bcc875_88.png)

![](img/40d99e508d30145a9e7e167a66bcc875_89.png)

![](img/40d99e508d30145a9e7e167a66bcc875_90.png)

![](img/40d99e508d30145a9e7e167a66bcc875_91.png)

The problem then becomes one that。

![](img/40d99e508d30145a9e7e167a66bcc875_93.png)

Your ellipse might not necessarily fit the data， so in this case， even having an ellipse。



![](img/40d99e508d30145a9e7e167a66bcc875_95.png)

You're still going to have。

![](img/40d99e508d30145a9e7e167a66bcc875_97.png)

Data from one that is in the other when it shouldn't be。



![](img/40d99e508d30145a9e7e167a66bcc875_99.png)

So really， that method isn't working。So what method might work then？



![](img/40d99e508d30145a9e7e167a66bcc875_101.png)

Given that this is the shape that you ultimately want in terms of your two different clusters。

 you want everything in。

![](img/40d99e508d30145a9e7e167a66bcc875_103.png)

Green to be one cluster， everything here in blue to be a second cluster。



![](img/40d99e508d30145a9e7e167a66bcc875_105.png)

The approach that would probably work best for this would be DB scan the way DB scan works is it looks at the density of the dots。

 not just the distance from a centroid， and it uses that to be able to calculate what's part of a cluster and by doing that it's actually able to get more interesting shapes for clusters and keep them separate so it can recognize something like this。



![](img/40d99e508d30145a9e7e167a66bcc875_107.png)

![](img/40d99e508d30145a9e7e167a66bcc875_108.png)

![](img/40d99e508d30145a9e7e167a66bcc875_109.png)

![](img/40d99e508d30145a9e7e167a66bcc875_110.png)

And so don't assume that all clustering methods behave the same。

 there are a number of different clustering methods that're based on different criteria and depending on what you have for data。

 some may work better than others。

![](img/40d99e508d30145a9e7e167a66bcc875_112.png)

![](img/40d99e508d30145a9e7e167a66bcc875_113.png)

K means tends to be used just because it's the simplest form to use。

 but there are other more advanced algorithms that can provide better results。



![](img/40d99e508d30145a9e7e167a66bcc875_115.png)

![](img/40d99e508d30145a9e7e167a66bcc875_116.png)

I had mentioned at the beginning I was going to talk a little bit about the difference between K means clustering and K nearest neighbors which often get confused。

So K meansan's clustering is exactly what it sounds like， it's a clustering algorithm。

 it is meant through trying to find different clusters of data and put those clusters together。

K nearest neighbors by contrast is a classification algorithm， it's given a single point。

 how do you classify that point？K means clustering。

 it will try to partition a set of points into these k sets or basically create K clusters based on what points are near to each other。

Kane nearest neighbors in contrast， says " I've got a point。

 I want to classify that point into one of these different clusters。

 based on the points that are nearest to it。And I'll give you an example of that in the next slide。

The other key point， the key difference is that key K means clustering is unsupervised。

 there is no external classification used， rather you have an entire set of points。

 you pick some k and then in an unsupervised manner。

 your algorithm goes and finds the clusters such that you have this minimized cost function so that you have a centroid that is close to all of the different points in its space and that that is never changing that you have a stable system。

sorry indifference to this， key nearest neighbors is a supervised algorithm because you already have these different clusters that are labeled or classified and you're trying to determine the classification of this new point。

 and so you can't determine that classification without having known the classification of other points previously。

So let's look at an example of this。Here we have two classes。

 we have the green squares and we have blue。Hexagons。So then the question is， if we have the point。

 which is this red star。Right here。

![](img/40d99e508d30145a9e7e167a66bcc875_118.png)

How is it that we should classify that point， should it be in class1， the green squares or class two。

 the blue hexagons？

![](img/40d99e508d30145a9e7e167a66bcc875_120.png)

![](img/40d99e508d30145a9e7e167a66bcc875_121.png)

The way we do that is by looking at its K nearest neighbors， so assume that we pick K to B3。



![](img/40d99e508d30145a9e7e167a66bcc875_123.png)

In that case， looking around what you'll see looking at this circle。



![](img/40d99e508d30145a9e7e167a66bcc875_125.png)

It defines where the three nearest neighbors are， so the green point， that blue point。

 and that blue point。

![](img/40d99e508d30145a9e7e167a66bcc875_127.png)

Based on that， you're going to do a voting system， you have two blue points versus only one green。

 and therefore you say that that new point belongs to class two， the blue hexagons。



![](img/40d99e508d30145a9e7e167a66bcc875_129.png)

![](img/40d99e508d30145a9e7e167a66bcc875_130.png)

If， however， you chose a different K， so you use k equal to5， what will happen instead？



![](img/40d99e508d30145a9e7e167a66bcc875_132.png)

Is that you look at this circle of here to get its five nearest neighbors， so one，2，3。Four and five。

And now during a majority voting rule， you'll see that green is considered to be the cluster that K or that this point should belong to。



![](img/40d99e508d30145a9e7e167a66bcc875_134.png)

So it should be class1 and not class2， and so the K that you choose will have an impact on what class。

 potentially what class a point gets assigned to。

![](img/40d99e508d30145a9e7e167a66bcc875_136.png)

![](img/40d99e508d30145a9e7e167a66bcc875_137.png)

The other thing to note here is that we chose K to be an odd number。

What would have happened if we'd taken K to B even？So for example， say we chose K to be2。

What are our two closest points then， well our two closest points would have been here and here？



![](img/40d99e508d30145a9e7e167a66bcc875_139.png)

And therefore， it would have been assigned to the blue class。In this case。

 that's not so bad because even with K equals to3， it still would have been chosen to be in the blue class。

 but what would have happened if， for example， green was actually the nearest point？



![](img/40d99e508d30145a9e7e167a66bcc875_141.png)

![](img/40d99e508d30145a9e7e167a66bcc875_142.png)

![](img/40d99e508d30145a9e7e167a66bcc875_143.png)

Then you're trying to do a majority rules except that you have a tie and so you can't decide which point it belongs to。

 so you always use an odd number so that you have a tie breaker。



![](img/40d99e508d30145a9e7e167a66bcc875_145.png)

![](img/40d99e508d30145a9e7e167a66bcc875_146.png)

That's assuming that you're using some sort of a voting system to determine what class a particular point belongs to。

 but that's usually the simplest way and so what tends to be used for Ka nearest neighbor。



![](img/40d99e508d30145a9e7e167a66bcc875_148.png)

![](img/40d99e508d30145a9e7e167a66bcc875_149.png)

So that explains K nearest neighbor and the difference between that and K means clustering。

 which is an unsupervised way of trying to determine clusters to begin with as opposed to classifying an individual point within a set of already known clusters。



![](img/40d99e508d30145a9e7e167a66bcc875_151.png)

![](img/40d99e508d30145a9e7e167a66bcc875_152.png)

![](img/40d99e508d30145a9e7e167a66bcc875_153.png)

And that concludes this particular module。

![](img/40d99e508d30145a9e7e167a66bcc875_155.png)
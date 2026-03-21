# 约翰霍普金斯大学《GPU编程（并发编程、并行编程、面向企业、CUDA高级库）｜GPU Programming》 p77 16_GPU排序算法伪代码-冒泡排序.zh_en -BV1a1421r7vw_p77-

We are going to use sorting algorithms。To look at GPU pseudocode and some of the challenges with this class of algorithms。

 which are not naturally well suited for GPus。While there are many sorting algorithms。

 we're going to focus on3 and three that yet again， are not naturally great fits for GPs， but are。

Very well known。 very well documented。 You can find pseudo code for them。

And implementations all over the Web。And there are implementations of these for the GPU。

 It just takes a lot of thought。They are bubble sort。

 which is sort of one of the easiest or simplest sorting algorithms， though not very efficient。

Radatic sort， which uses the actual， you know sort of numeric representation of columns or parts of the data to sort。

 and then Quick sort， which by its name says I'm going to be pretty quick， and it is。

 though yet again， not the best fit for out of the box translation into GPU code。



![](img/452b6e8d25f5caf64a3cae2030829569_1.png)

![](img/452b6e8d25f5caf64a3cae2030829569_2.png)

![](img/452b6e8d25f5caf64a3cae2030829569_3.png)

So let's look at an animated g showing how bubble sort works。



![](img/452b6e8d25f5caf64a3cae2030829569_5.png)

One of the things you'll notice is that it does pair wise comparison。Moving left to right。

This seems natural。 You just have a four loop that's going to go through and say， okay。

4 x iterate through the index， compare it to the one before it or after it based where x is。



![](img/452b6e8d25f5caf64a3cae2030829569_7.png)

And this is nice from the perspective of a human understanding。



![](img/452b6e8d25f5caf64a3cae2030829569_9.png)

What you'll notice is that。You're going to have to do multiple passes through this algorithm because the first time you go through it。



![](img/452b6e8d25f5caf64a3cae2030829569_11.png)

You've just， sort of。To move things around So somewhat。



![](img/452b6e8d25f5caf64a3cae2030829569_13.png)

Ordered in that the very last。Value should be the highest value。

And you're going to have to go through this until every single。



![](img/452b6e8d25f5caf64a3cae2030829569_15.png)

Item is in its appropriate place。

![](img/452b6e8d25f5caf64a3cae2030829569_17.png)

Which means that it has to run。 Think of it。 There are  eight items in this。 It has to run。

8ight times some number of items because each time it has to go through。 So it has to 8，7，6，5，4，3，2。

1 comparisons。 and that's like， you know， it's going be if you've done。

Statistics you'll have an understanding of what that is， but it's definitely closer to say。N。

 which is 8 in this case， times 7。 so n minus1。 so it's almost a squared algorithm。

 it's not oh of n squared exactly， but it's pretty darn close。



![](img/452b6e8d25f5caf64a3cae2030829569_19.png)

And the one nice thing about it is the size of the data determines how efficient the algorithm is。

 but it actually doesn't vary based on the complexity of the data。



![](img/452b6e8d25f5caf64a3cae2030829569_21.png)

![](img/452b6e8d25f5caf64a3cae2030829569_22.png)

So the thing to consider here when we're looking at the serial code is it's two four loops。

 that gets really hard for a。GPu。Its first thing you can think of is maybe the outside for loop can become for loop in the host code and that that is an iteration right。

 as you saw in the video of how the pseudocode should work is that you're going to scan across all the data。

And then you're going to do another scan of a smaller side of the data。

 So let's think of that outside for I as a loop in the host code。Now， the for loop， the four index。

 that inside loop。 can you can consider that being。An internal or pur。Thread GPU device。Colonel。

And you can just have maybe what you can do in this case is use shared memory。

And something like for the bullolean swaps， you can consider that to be something。

 and we'll go over this in detail or considering memory allocation。

 But maybe what you do is you have something that everything all the threads look at。

 They do subordinate swaps as needed， and they look at each other。

 like the state of their index or another index to determine if they should continue。



![](img/452b6e8d25f5caf64a3cae2030829569_24.png)

![](img/452b6e8d25f5caf64a3cae2030829569_25.png)

![](img/452b6e8d25f5caf64a3cae2030829569_26.png)

![](img/452b6e8d25f5caf64a3cae2030829569_27.png)

![](img/452b6e8d25f5caf64a3cae2030829569_28.png)

Un lesson to learn from even the simplest CPU to G view code translation is。



![](img/452b6e8d25f5caf64a3cae2030829569_30.png)

It's not always automatic， and you definitely have to think about it。

 you have to think about it even more as we get to more complex algorithms。



![](img/452b6e8d25f5caf64a3cae2030829569_32.png)
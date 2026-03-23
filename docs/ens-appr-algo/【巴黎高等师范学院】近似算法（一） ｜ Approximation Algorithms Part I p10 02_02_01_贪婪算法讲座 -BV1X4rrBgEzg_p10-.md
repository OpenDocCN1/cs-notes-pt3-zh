# 【巴黎高等师范学院】近似算法（一） ｜ Approximation Algorithms Part I p10 02_02_01_贪婪算法讲座 -BV1X4rrBgEzg_p10-

。

![](img/105d0e30f9053373cc4cb60b4cf0105a_1.png)

We have defined the NApsaro， and we have decided to temporarily focus on a special case where every item has its size equal to its value。

Let us design a algorithm for this special case。This case seems easy。

We want to maximize the value of what we take in。 How about us trying to take the items。

By decreasing value， starting with the most valuable item。How good is that algorithm。

This is another version of the greedy algorithm， the greedy algorithm that takes item by order of decreasing value。

Graphically， the case when size equals value is the case when every item is a square instead of just a rectangle。

😊，And our algorithm is sort the squares by decreasing size and then take them one by one greedily if they fit in the knapsack。

 If the sum of the heights is less than B。😊，Observe。The total height。

Is less than B for every solution。Including the optimal solution。So。Opt is also less than B。

 The optimal solution has value equal to its height。 That is at most。B。Up is lesson B。

That's the first observation we have seen in previous lectures that one way to analyze an approximation algorithm is to relate opt to some parameter。

😊，Then relate our output solution to that parameter。

 So now we need to look at our output and compute its value as a function of B。😊，Observe。

If we take the output and we add any item that's been rejected。

 it's been rejected because it did not fit because the sum of the values was greater than B。😊。

We can assume that the output has at least one item。 We can assume that in this picture。

 where the items in the output are blue and the rejected item， one of the rejected items is red。

We can see that there's at least one blue item。Why。Why， because if there were no blue items。

 what would it mean， It would mean that nothing fits in the knapsackack。

 and then Opt also would put nothing in the knapsack。 and so。Our output would be0。Up to B also 0。

 So which is optimal。Observe that we can also assume that there's at least one red item。

 There exists some item that does not fit in an knapsackack for the solution that we are constructeding。

 constructing。 Why not。Well。😮，If。The Napsa contained every item。 Then， of course。

 it would be optimal。 How could you do better than take everything。

So we can assume that the output has at least one item and the non output has at least one item。

And then there's at least one red rectangle。 There's a bunch of blue rectangles。

 The output plus one item is greater than B。Okay， so then think about the order in which we took the items。

 What was the first item we put in the output。The first item。Look at it。It's big。

It's bigger than this one。The first item in the output is bigger than any item， not in the output。

 Why proof by picture。Wai。Because the first item is the largest item that can fit in annapsack。

So the output plus the right item is greater than B。

The first output item is greater than the red item。Therefore， combining。

 we can deduce that the output has valued at least half of B， at least B over 2。And now， remember。

Output lower than the other two。Opt less than B， less than or equal to be。Combine。

Output larger than up of2。There is a factor of 2。We have proved a theorem。

In a special case where the size is equal to the value。

 this greedy algorithm is a true approximation。 Obviously， it's polynommal time。

 It's basically at the time it takes to sort， and it's correct。

 It gives you something that does fit in an Epsack。😊，Not good enough。I'm not happy with this。

I want better than the two approximation。Can we do better， How can we do better。

 This will be the object of the next section。 So we have seen a two approximation for the special case when the size is equal to the value。

 And in the next section， we will try to develop something much better than a two approximation。😊。



![](img/105d0e30f9053373cc4cb60b4cf0105a_3.png)
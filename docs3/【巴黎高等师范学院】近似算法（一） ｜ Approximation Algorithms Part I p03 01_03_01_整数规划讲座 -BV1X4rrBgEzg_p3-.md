# 【巴黎高等师范学院】近似算法（一） ｜ Approximation Algorithms Part I p03 01_03_01_整数规划讲座 -BV1X4rrBgEzg_p3-

。

![](img/081f12620a7774abf969a8957cbf5799_1.png)

I have given you the definition of the vertex cover problem。I showed you the input。

 I showed you the output that defines the problem。Now we are going to see in more depth a mathematical formulation for the problem as an integer program。

😊，An literature program has three parts to it。Variable。Constraints。And an objective。

Let us start with the variables for modeling the but cover problem。

A vertex cover is a subset of all the vertes in the graph。How do we model。

 How do we represent a vertex cover。Well， how do we represent a subset of what is of the graph？

For each vertex of the graph， we need to know whether or not the vertex is in the subset。

 two possibilities。So， let us define one variable。For each vertex of the graph。

Vertex a gives us variable x sub a。That takes on two possible values，0，01。Depending on weather。

Forertex a is in the subset， X a equals 1。Means vertex A is in the cover。X a equals 0 means。

Fortex a is not in the cover。We do this for every thetex in the graph。N for this is。

 This gives us n variables。Two possibilities for each variable。

 this gives us two to the n possible assignments of our variables。So that's our variable set。😊，Next。

The constraints。A vertex cover must cover every edge in the graph。😊。

How do we capture that mathematically with an algebra expression。Let us consider one of these edges。

 say edge A B。We have two variables， X sub B， X sub B。Each of them takes on two possible values。

 so we have four possibilities。4 possibilities。0，0，1，0，0，1，1，1。In the first case，0，0。

Neither A nor B are in the cover。 And so the edge is not covered。In the other three cases。

 the edge is covered。Now， what we need is an idea。The idea is。

 let us compute the sum x sub B plus x sub B。And observe in these four possibilities。

 what do we have0 plus 0 equals 0 in French， we say0 per0 e Lateta totu。😊，1 plus 0 is 1。

0 plus 1 is 1，1 plus 1 is 2。 So the four possibilities for the sum are 0，1，1，2。

And we want to express the fact that。The bottom three are a cover of the edge。

 The first one is not valid。Very simple。 X sub B plus X sub B is greater than equal to1。

 This expresses the fact that our vertices cover the edge， A B。

Going from one edge to an entire graph， we write one constraint for each graph edge。

 And so we have the whole set。Of constraints， of linear inequalities that together。

Express the fact that the subset of the vertices is a vertex cover。Finally。

 we want the vertex cover that has minimum weight。 How do we write this。

 We write this using an objective。 The objective is to minimize。😊，X sub a times 1。Because。

If a is in the cover since a has weight 1， it contributes1 to the cost plus x sub B times 4。

 If B is in the cover， it contributes 4 to the cost plus 4 x E plus 2 x D plus 9 x E plus 4 xf plus 3 xg。

That's it。 That's our objective。What is the relation to recap if you look at the green vericees。

 ACDFG。Observing the graph， you can see that every edge is covered。 It's a vertex cover。

Suming their weights， you can see that the value is 14。Corresponding to that。

 there's an assignment of the variables， X， A， X， E， X， D， X， F， X G are all equal to1。

 and the other variables are equal to 0。You can verify that all the inequalities are satisfying because all edges are covered。

😊，And that the value of the objective is。f钱啊。In general， for our general graph。

You have one variable per vertex。 You have the constrain that for every vertex in your graph。

 every vertex U variable X U must be equal to 0 or equal to 1。And for every edge of the graph。

 you have the constraint that if the edge is Uv， X U plus x v has to be greater than equal to 1。

Given these constraints， your objective is to minimize the sum over every vertex u in the graph of w sub times x U。

This is an individual program。😊，4 vertex cover。There's a one to one correspondence between vertex covers and assignments of variables that satisfy all the constraints。

And the value of the vertex cover is the objective value of the corresponding assignment。Thus。

 I have given you an nteger program。That is a formulation for the vertex cover problem。Now。

 we are going to see a linear programming relaxation for vertex cover。😊。



![](img/081f12620a7774abf969a8957cbf5799_3.png)
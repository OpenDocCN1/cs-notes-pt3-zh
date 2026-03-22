# 【加州大学圣地亚哥分校】机器学习基础  Machine Learning Fundamentals p57 12-03-02-前馈神经网络 -BV1TyFSziEZb_p57-

![](img/01a949f8f0051744b01df48718da6e39_0.png)

Today， we will talk about speed forward neural nets。We'll see what these nets look like。

 how they are parameterized， and what kinds of functions they are able to express。



![](img/01a949f8f0051744b01df48718da6e39_2.png)

![](img/01a949f8f0051744b01df48718da6e39_3.png)

So a fitfall with is inspired loosely by the neural circuitry of the brain。嗯。

So generically it looks something like this， a large graph。



![](img/01a949f8f0051744b01df48718da6e39_5.png)

Each node in the graph is often called a unit。And these units are organized into layers。

At the very bottom is the input layer Okay， so if we are dealing with data that is a D dimensional。



![](img/01a949f8f0051744b01df48718da6e39_7.png)

Then this input layer contains D units， one for each of the features of the input X。

 so there's a unit for x1 for x2， for x3， all the way to X D。



![](img/01a949f8f0051744b01df48718da6e39_9.png)

So the input is presented at the bottom。And then various computations are done in a bottom to top pass and the output comes out all the way at the very top。

So what's going on in the middle？

![](img/01a949f8f0051744b01df48718da6e39_11.png)

Well， the other notes？The ones that aren't inputs or outputs are called hidden units and they organize into layers。



![](img/01a949f8f0051744b01df48718da6e39_13.png)

![](img/01a949f8f0051744b01df48718da6e39_14.png)

Okay， so there's。Hidden layer number one。And hidden layer number two。

 and in this picture all the way up to hidden layer number L。



![](img/01a949f8f0051744b01df48718da6e39_16.png)

Given the inputs， the first thing we do is to compute the values of the units in hidden layer number one。



![](img/01a949f8f0051744b01df48718da6e39_18.png)

Then we use those to compute the values in hidden layer number two and so on and so forth until we get to the very top。



![](img/01a949f8f0051744b01df48718da6e39_20.png)

Okay， so how are these values computed， however， okay？Well。

 let's look at any internal node in this graph， let's look at this node for example。

It has connections to various nodes in the previous level， in this case， three of them。

 and these are the three connections。We'll call those notes its parents。

And the value at that node is a function of the values of its parents。😊，Okay， so in particular。

 once we know the input layer， we can simply apply this function to compute the values in the first hidden layer。

😊，So what are these functions exactly， Well， let's pick one node particularly called it H。



![](img/01a949f8f0051744b01df48718da6e39_22.png)

How do we get the value of H， given the values of its， in this case， three parents？



![](img/01a949f8f0051744b01df48718da6e39_24.png)

![](img/01a949f8f0051744b01df48718da6e39_25.png)

Okay。Okay。So let's look at a hidden unit and let's say that it's got end parentss okay。😊。

Given the values of those parents。The way we get H is very simple。 For the most part。

 it's just a linear function。 so what we do is we start by computing a linear function of Z1 through Zm。

 So a function of the form W1 Z1 plus W2 Z2 plus WM Zm plus an offset B。



![](img/01a949f8f0051744b01df48718da6e39_27.png)

So we compute that linear function， which gives us a real number。And then at the end。

 we apply a nonlinear activation function to the answer。

And that's what I'm denoting over here by Sigma。Okay， so what is this activation function Sigma？



![](img/01a949f8f0051744b01df48718da6e39_29.png)

Well， for instance， it could just be the squashing function of logistic regression。

But in the setting of neural nets。The activation function that's used most commonly is what's called a rectified linear function。

And it's specified by this simple rule over here。It takes a real number。

And if the number is positive， it keeps the number。



![](img/01a949f8f0051744b01df48718da6e39_31.png)

If the number is negative， it returns 0。Okay， so if we were to draw a graph of this。

 it would look something like this。

![](img/01a949f8f0051744b01df48718da6e39_33.png)

We have a number U， and we want to compute。The rectified linear function of U。If U is negative。

 we return zero。

![](img/01a949f8f0051744b01df48718da6e39_35.png)

![](img/01a949f8f0051744b01df48718da6e39_36.png)

And if he was positive。Then we just return you。

![](img/01a949f8f0051744b01df48718da6e39_38.png)

So we get something like this。Okay。So let's summarize。The function that gives us H。From its parents。

 Z1 through ZM is parameterized by W1 through WM and by an offset B。We can in fact。

 imagine that W1 through WM weights on these edges。W1， W2 old way to WM。

So what we do is we compute z1 times w1。Z2 times W2 Zm times WM， we add them up， we add B。

 that's all linear function。And then we look at the result， which is some real number。

 if it's positive， we keep it， if it's negative， we return zero okay？And that is H。



![](img/01a949f8f0051744b01df48718da6e39_40.png)

Okay。So this is a graph again。And now we know how to get from。



![](img/01a949f8f0051744b01df48718da6e39_42.png)

Any node from any layer to the next layer。We just compute the value of each node as a function of the values of its parents。



![](img/01a949f8f0051744b01df48718da6e39_44.png)

No。Now， what was the need for having nonlinear activations？

Why not just have linear functions the whole way， why do we need those sigmas？Well。

 suppose we just had linear functions in that case。

 the entire layer H1 would just be a linear function of x。

And the entire layer H2 would just be a linear function of H1 and H3 would be a linear function of H2。



![](img/01a949f8f0051744b01df48718da6e39_46.png)

Now a linear function of a linear function is again， a linear function。😊，So in this case。

 H2 would be a linear function of x， and in fact， any node in the entire graph would just be given by a linear function of x。



![](img/01a949f8f0051744b01df48718da6e39_48.png)

The entire computation of the network could be summarized by a linear function and there would be no need for any hidden units at all。

やく。So in order to make use of a hierarchy like this with multiple hidden units。

 it's essential to have nonlinearities of some form in there。😊，Okay。Okay。

 so we've seen how to obtain values at。All of the hidden layers。

 But what happens at the outdoor trail。

![](img/01a949f8f0051744b01df48718da6e39_50.png)

How are those values obtained？

![](img/01a949f8f0051744b01df48718da6e39_52.png)

So for concreteness， let's say that what we' are trying to solve is a classification problem in which there are K possible labels。

In that case， what we would do is that we would most likely have k units in the output layer。

Y1 through YK1 unit corresponding to each possible label。

And what we want is the probability of each label。 So given an input X。

 we would want to know what is the probability of label 1 given x。

 the probability of label 2 given x all the way to the probability of label K。

So how do we do this Well the first thing we do is that we've just let each y be a linear function of its variance。

😊。

![](img/01a949f8f0051744b01df48718da6e39_54.png)

Okay。So we end up with K real numbers， y1 through yk。But these could be numbers like minus 2。3 or 6。

7。 how do we convert them into probabilities？Well， we do this exactly the same way that we did for multiclass logistic regression。

We just use a softm function。嗯。So after we've computed these values， y1 through YK。

In order to get probabilities， what we say is that the probability of a particular label like label J。

I's proportional。To E to the Yj。Okay， so the most likely labeled are the ones for which the corresponding y value is the largest。

And the specific probability is just the normalized version of e to the Yj。

 namely e to the yj divided by e to the y1 plus all the way to e to the Y K。Okay。

So this is very familiar， just like logistic regression。In a sense。

 that last layer of the network is simply implementing multiclass logistic regression。



![](img/01a949f8f0051744b01df48718da6e39_56.png)

Okay， now let's think a little bit about how many parameters there are overall in a neural net like this。



![](img/01a949f8f0051744b01df48718da6e39_58.png)

![](img/01a949f8f0051744b01df48718da6e39_59.png)

Okay。

![](img/01a949f8f0051744b01df48718da6e39_61.png)

So let's see， we saw that each node。

![](img/01a949f8f0051744b01df48718da6e39_63.png)

Is a linear function of its parents plus a nonlinearity。



![](img/01a949f8f0051744b01df48718da6e39_65.png)

If a node for example， has got three parents。Like this one。

Then it has its own linear function with four parameters， one for each parent。

 and then an offset term。

![](img/01a949f8f0051744b01df48718da6e39_67.png)

So even if we ignore the offset term， there is at least one parameter per edge of the graph okay so the number of parameters in the neural net is at least the number of edges。



![](img/01a949f8f0051744b01df48718da6e39_69.png)

So how many edges are there？

![](img/01a949f8f0051744b01df48718da6e39_71.png)

Well， why don't we do something a little bit concrete Okay， let's say the input is of moderate size。

 say  a thousand dimensional。

![](img/01a949f8f0051744b01df48718da6e39_73.png)

![](img/01a949f8f0051744b01df48718da6e39_74.png)

Now hidden layers could be of any size， they could be hidden layers of size 20 or of size 10，000。



![](img/01a949f8f0051744b01df48718da6e39_76.png)

![](img/01a949f8f0051744b01df48718da6e39_77.png)

So let's just say for concreteness that we have two layers that are both of size 1000。

 so a layer with a thousand0 nodes and another layer with 1 thousand0 nodes。

 and let's say that they are fully connected。

![](img/01a949f8f0051744b01df48718da6e39_79.png)

Okay。How many edges do we have between them？

![](img/01a949f8f0051744b01df48718da6e39_81.png)

Well， if they each have a thousand nodes， then the number of edges is a thousand times a thousand。

 in other words a million。

![](img/01a949f8f0051744b01df48718da6e39_83.png)

And that's just one layer of the network。

![](img/01a949f8f0051744b01df48718da6e39_85.png)

So as you can see， the number of parameters in a net like this can easily be enormous。



![](img/01a949f8f0051744b01df48718da6e39_87.png)

Great。And this immediately means two things。Okay， so first of all。😊。

These networks are extremely expressive。They can express a wide range of different functions。

And second， it's clear that we're going to need quite a lot of data in order to learn all of these parameters。

Okay， so let's now talk a little bit about the depth of the network。Okay。

How does the depth influence the expressiveness of the net？

The range of functions that it can compute。

![](img/01a949f8f0051744b01df48718da6e39_89.png)

So there's a very well known result。Which says that a neural net with just one hidden layer。



![](img/01a949f8f0051744b01df48718da6e39_91.png)

Can compute any function。To arbitrary accuracy， Okay。

 so it can arbitrarily well approximate any function at all。



![](img/01a949f8f0051744b01df48718da6e39_93.png)

That sounds very powerful。And it also raises the question of why we would ever want to use more than one hidden layer if we can get any function with just one layer。



![](img/01a949f8f0051744b01df48718da6e39_95.png)

Why would we ever need more layers？Okay。So that's a very good question。

 and it's not something to which there is a completely definitive answer。

But here's one thing that we can say so one thing that people have pointed out。

Is that there are certain functions that you can write down。And if you and of course。

 you can approximate them by a one layer network， a network with one hidden layer。

 but if you do that， the hidden layer has to be enormous， the number of nodes。

 the number of hidden nodes in that one layer has to be， for instance。

 exponential in other problem parameters， such as the input dimension。

But if instead you use a deeper network。Then each of the individual layers can actually be of moderate size。

😊，So that's one way in which depth can be quite helpful。Okay， that's good for now。



![](img/01a949f8f0051744b01df48718da6e39_97.png)

We have seen what a feed forward neural net is。And next time。

 we'll talk about how to learn the parameters of a net like this。See you点。


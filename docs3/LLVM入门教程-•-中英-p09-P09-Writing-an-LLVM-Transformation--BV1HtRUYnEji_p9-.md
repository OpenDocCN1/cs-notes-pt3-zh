# LLVM入门教程-•-中英-p09-P09-Writing-an-LLVM-Transformation--BV1HtRUYnEji_p9-

![](img/a4e08325a5471bf55745b356398ec9be_0.png)

Hi， everyone。 In the previous video， we just showed you how to write an novel VM analysis best。



![](img/a4e08325a5471bf55745b356398ec9be_2.png)

In this video， we will use the analysis Liger wrote to implement a transformation pass。



![](img/a4e08325a5471bf55745b356398ec9be_4.png)

First， a brief recap。The analysis traverse is a function。

 collecting editions that only use calls tinages。Now。

 our transformation will remove the instructions and replace their users with a precompd sum computed at compile time。



![](img/a4e08325a5471bf55745b356398ec9be_6.png)

Let's get to the code。 The first step is updating our header file to include a new ad con faststruct。

This will look very similar to the add cost printer pass we have defined last time。

Except this truck won't need any private variables。



![](img/a4e08325a5471bf55745b356398ec9be_8.png)

Next， we make a new file where we implement our transformation tests。

Remember to update your CMake list find included as well。Similarly to our analysis。

 our transformation needs a run function。This functions returns a preserved analysis object。

This object represents the set of analysis that are preserved following a run of a transformation pass。

We will explain this in a more detail， in a bit。The first thing we do is get the result of our analysis。

At In is the vector of the instructions that is collective。

We then iterate over the add instructions collected and called a replace add in with constant function。

 which we'll define later， passing them as a parameter。



![](img/a4e08325a5471bf55745b356398ec9be_10.png)

Now， it's simply a matter of returning the preserved analysis。



![](img/a4e08325a5471bf55745b356398ec9be_12.png)

We start with a preserved analysis object that represents all the analysis。



![](img/a4e08325a5471bf55745b356398ec9be_14.png)

![](img/a4e08325a5471bf55745b356398ec9be_15.png)

We then abandoned the ad constant analysis since the ad instructions collected or deleted from the program。

This means that any other FA that requires at constant analysis will cause the analysis through run again。



![](img/a4e08325a5471bf55745b356398ec9be_17.png)

![](img/a4e08325a5471bf55745b356398ec9be_18.png)

Then we simply returned the preserved analysis。Now。

 let's take a look at the replace set ins with constant function。

 which is where the real work is done。

![](img/a4e08325a5471bf55745b356398ec9be_20.png)

We start by extracting the first opera of the addition and cast it to the constantin type。

We do the same thing for the second argument。We now compute their sum and place that in a sum variable。

Now， we replace the uses of the results of the adding instruction with there some we just computed。



![](img/a4e08325a5471bf55745b356398ec9be_22.png)

Then we erase the adding instruction from the program。 And， and with that， we are done。



![](img/a4e08325a5471bf55745b356398ec9be_24.png)

The last step is to register our analysis。 This is how a simplified version of our register pipeline function looked like last time。

We insert a check if the name is at Kt， and in that case we have our transformation in the pipeline。



![](img/a4e08325a5471bf55745b356398ec9be_26.png)

Let's run our transformation pass on the example file， when they find beforehand。As a reminder。

 this is what the example looked like initially。Again， we use Oc to run our path。Like last time。

 we have to load our plug first。Then we specify the name of the pass we'd like to run。

The S flag says we'd like the output to be the actualual representation。We specified the input file。

And we specified the output file to be Futu in the examples folder。



![](img/a4e08325a5471bf55745b356398ec9be_28.png)

And this is how our transform program looks like。Let's compare our function's body before and after each transformation。

On the left， we have the program before the transformation。On the right， the one after。First。

 notice how CD are now missing。

![](img/a4e08325a5471bf55745b356398ec9be_30.png)

And second， knowledge is how the appearance of the a instruction that defines F changed。

But we could actually go one step further。Notice at this point。

 F could also be computed at compile time and removed from the program。



![](img/a4e08325a5471bf55745b356398ec9be_32.png)

Let's see the in action。Let's rerun out。

![](img/a4e08325a5471bf55745b356398ec9be_34.png)

But now let's specify the input file to be full 2 and output file to be full free。



![](img/a4e08325a5471bf55745b356398ec9be_36.png)

And this is the final version of our transformed program。

Although we could have designed our transformation to iterate over the function until there were no more additions to remove。

This demonstrates how a real transformation could be potentially called multiple times when compiling a program。



![](img/a4e08325a5471bf55745b356398ec9be_38.png)

And with that， we conclude how to ride a transformation pass on top of all of VM。

This type of constant propagation is actually done automatically by LVM。

 even though no optimizations are enabled。 But we think it's a nice example of how to use the LVM's infrastructure to write your own passes。



![](img/a4e08325a5471bf55745b356398ec9be_40.png)

![](img/a4e08325a5471bf55745b356398ec9be_41.png)

In the next video， we'll see how to write the LLVM base2。Feel free to send any comments or questions。



![](img/a4e08325a5471bf55745b356398ec9be_43.png)
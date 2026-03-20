# 【精译⚡算法导论】AbdulBari p68 p67 7 Branch and Bound Introduction -BV1hhPXeTEWM_p68-

The topic is branch and bound。This is one more problem solving strategy。

 a method by which we can solve a problem this is similar to backtracking in the sense that it also uses a state space tree for solving the problem solutions is represented like a state space tree。

But。It is useful for solving optimization problem。And only minimization problem。

 not maximization problem。Anyway， we can convert a maximization problem into minimization and we can solve it。

So let me show you how it works。See， I have taken one simple example here。

 That is job sequencing with the deadlines problem。 Now。

 how the state space tree is generated for that one。

 There are two methods of generating a tree that depends how you want the solution。 See。

 suppose I say that I am doing job one and job4， this is my solution。

 Then the solution can be represented as subset of that jobs。

 This is one method of giving a solution。 And second method of representing a solution is First job is done。

 Second and third job is not done for job is done。

![](img/adfad02d6936167ddb2c5257d6850c48_1.png)

![](img/adfad02d6936167ddb2c5257d6850c48_2.png)

![](img/adfad02d6936167ddb2c5257d6850c48_3.png)

![](img/adfad02d6936167ddb2c5257d6850c48_4.png)

![](img/adfad02d6936167ddb2c5257d6850c48_5.png)

So this is variable size solution。 This is fixed to size solution。 See， as for this example。

 I got subset as two jobs。 Sometime I may get a three jobs or some problem， I may get just one job。

 So this is variable size。 But this type of solution。 If you write a solution like this。

 then it will be fixed size。 always will be representing zeros or ones equal to the number of jobs。

 right， there are two methods of solving this one or drawing a state space3。

 I will follow this method first， that is subset method。 Then that is a variable size solution。

 So for that， I can draw a state space 3 and。

![](img/adfad02d6936167ddb2c5257d6850c48_7.png)

![](img/adfad02d6936167ddb2c5257d6850c48_8.png)

![](img/adfad02d6936167ddb2c5257d6850c48_9.png)

I'll say that。Im。Considering for a job。Then。In backtracking， we will consider the next level。

 but here in Bran and bound， we will also consider second shop。



![](img/adfad02d6936167ddb2c5257d6850c48_11.png)

And then， third job。And then， for the job。

![](img/adfad02d6936167ddb2c5257d6850c48_13.png)

So it is like breadth first search。 We don't go depth wise。 we don't follow depth first search。

 We follow breadth first search for exploring the solutions of a problem。

 So the difference between backtracking and branch and bound is Backtracking was depth for search and the branch and bound is a breadth first search。

 Now， this one level is complete at C， I have considered all the jobs 1 by one。 Now。

 once I take first job， then what are the solution。 Jo 2， I can take or job 3， I can take。

 then job 4 I can take。

![](img/adfad02d6936167ddb2c5257d6850c48_15.png)

![](img/adfad02d6936167ddb2c5257d6850c48_16.png)

Right， first job is all taken， then I can take second job or third job or full job。

So if I follow one of the route， it says that I am doing first job and full job。

 I am not taking second and third job， that is the meaning。Now， which is the next？

And these nodes are 6，7，8。 Now， next， which node I should expand。

 Shall I expand this one or this one。 So next is this one。

I am doing second job considering second job， but what about the next one。

 I will be doing third job or fourth job。See first job already we have discarded。

 we are not considering it， we are not taking it， then third job and full job。

 then here only fourth job。

![](img/adfad02d6936167ddb2c5257d6850c48_18.png)

![](img/adfad02d6936167ddb2c5257d6850c48_19.png)

11th node。 Now， which node I should expand next， this node I should expand。

 So third job or fourth job。And if I expand this， I'll have only food job。Right。

 then this one is already fourth job here。 I can consider fourth job 16。 then all are reaching till4。

 and this is the last one17 fourth job。 So this is a state space tree for the solutions。

 if you're looking like this。 And if I consider any node。

 this node says that I am considering second job and fourth job。

 this node says that I am considering third job and fourth job。

 So this is one way of generating entry。 So branch and bond we generate a trail like this。

 This is one method。

![](img/adfad02d6936167ddb2c5257d6850c48_21.png)

![](img/adfad02d6936167ddb2c5257d6850c48_22.png)

![](img/adfad02d6936167ddb2c5257d6850c48_23.png)

![](img/adfad02d6936167ddb2c5257d6850c48_24.png)

Then I will show you second method of this one let us look at second method for the same variable size solution。

 see first node is generated and we consider first job job one and then job2。



![](img/adfad02d6936167ddb2c5257d6850c48_26.png)

No， one thing。 while generating this， I'll put this nodes in the stack。 Second node generated。

 third node generated。 Then I'll consider job 3。 This is the fourth note， fourth node in the stack。

 Then I'll consider job 4。 So this is the fifth node， fifth note。



![](img/adfad02d6936167ddb2c5257d6850c48_28.png)

![](img/adfad02d6936167ddb2c5257d6850c48_29.png)

![](img/adfad02d6936167ddb2c5257d6850c48_30.png)

![](img/adfad02d6936167ddb2c5257d6850c48_31.png)

Now， which node I should expand next， I should expand fifth node how the nodes I am keeping them inside the stack。

 So pop out this one and expand see already this is on the last job。

 There is no expansion possible further。 so pop out next node。



![](img/adfad02d6936167ddb2c5257d6850c48_33.png)

![](img/adfad02d6936167ddb2c5257d6850c48_34.png)

![](img/adfad02d6936167ddb2c5257d6850c48_35.png)

And expand this one。 So which job job for， third is over，4 is over， right，4。 So node 6。

Now which node I should explore next， that sixth node。So can it be explore further node。

 This is the last job。 Okay， pop out the next node and explore it。 See this is second job。

 So what possible third job， right， or fourth job。

![](img/adfad02d6936167ddb2c5257d6850c48_37.png)

This is node 7 and8， push both of them in the stack。Now， which node I should explore。8 node。

 This is already on fourth job。 It cannot be expanded further。 Then seventh node。 Yeah。

 I can expand it。 job 4。 This is 9 node，9 node。

![](img/adfad02d6936167ddb2c5257d6850c48_39.png)

Which node I should explore next， so take it out from the stack9， it cannot be explored further。

 so take out two and explore it。

![](img/adfad02d6936167ddb2c5257d6850c48_41.png)

So exploration first job is done。 second job or third job or fourth job。So the node numbers are 10。

11 and 12， and in the same order they are pushed into the stack。



![](img/adfad02d6936167ddb2c5257d6850c48_43.png)

![](img/adfad02d6936167ddb2c5257d6850c48_44.png)

So this is another method。 So what is the difference in the previous one and this one in the previous one we were using Q。

For next node exploration。 And now we are using stackg for next node exploration。

 So if you are using Q， then it is called as fifo branch and bound。 And if you are using stackg。

 then it is called as LiO branch and bound。

![](img/adfad02d6936167ddb2c5257d6850c48_46.png)

So you can use anyone and you have to follow breakfast search only What is breakfast search here once you pick up a node for exploration you should explore all the possible nodes then only you should select the next node。

That's what breakfast searches。 So what next node from where you select you select from Q also stack also。

And there is one more method one。 That is least cost branch and bound。 So this is L branch and bound。



![](img/adfad02d6936167ddb2c5257d6850c48_48.png)

![](img/adfad02d6936167ddb2c5257d6850c48_49.png)

There is one more method。 I'll show you that one now。 Now， let us look at this method。

 lease cars branchn and bound method。 So for this problem。

 I will generate a tree again states pastry。Let us start with first point。

Now this time I will explain you one more new thing that is for every node we will calculate the cost。

 so what is cost depending on the problem we define a cost function and using that function we find out the cost of each node。



![](img/adfad02d6936167ddb2c5257d6850c48_51.png)

And this we do for all three meters， whether you are using P4 or V4 or LC。

 then only we can solve a minimization problem。

![](img/adfad02d6936167ddb2c5257d6850c48_53.png)

Let us assume the cost of this one is infinity。 Now let us consider the jobs。



![](img/adfad02d6936167ddb2c5257d6850c48_55.png)

First job。Right and the cost of this node is let us say 35 just randomly。

 I'm writing some number then。

![](img/adfad02d6936167ddb2c5257d6850c48_57.png)

Secondd job。The cost of this is。对完了。And this one。 Third job。The cost of this one is。不。19。

And next for the job， note 5， let us say cost of this is 30。



![](img/adfad02d6936167ddb2c5257d6850c48_59.png)

Now which node I should explore next， the node with the minimum cost I should explore next。

Leased cause。 That's what it is。 least cause branch and bound。 So here of least cause this one。

 So I should explore this one。

![](img/adfad02d6936167ddb2c5257d6850c48_61.png)

Now， let us look back again。 P4 method， which one we select it for exploration。

 This one will expand Le4 will try to expand this one。 lease course out of this。

 whichever is having lease course will try that one。 So we'll expand this one。So job  two is there。

 So this is job 3 and job4。 Suppose here the cost is8 and here the cost is 7。

Now which one we should explore this one， but this is the last note， second job， fourth job。

 so this is the solution。So like this， instead of generating entire tree。

 we always pick up the nodes with minimum cause。 That is least cause and try to explore that one so that quickly we can reach the solution。

 This is the idea of L branch and bound。 And this is much faster than using P4 and LeO。

 We can use any of these methods。 But in each method。

 we write on the cost of each node and find the solution。 Then in coming videos。

 I'll be solving few problems using branch and bound。😊。



![](img/adfad02d6936167ddb2c5257d6850c48_63.png)
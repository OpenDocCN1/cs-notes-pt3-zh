# 【精译⚡算法导论】AbdulBari p69 p68 7.1 Job Sequencing with Deadline - Branch and Bound -BV1hhPXeTEWM_p69-

The problem is job sequencing with deadlines。This problem can be solved using branch and bone。

 even this problem can be solved using greedy method and dynamic programming。

But let us learn how it can be solved using branch and bound。

 but one thing we should remember that branch and bound is useful for solving minimization problem。

 it cannot solve maximization。If you know something about job sequencing with deadline。

 it is a maximization problem like profits are given for the jobs and we want the maximum profit。

 so we have converted the problem in stuff profit we are taking penalty here。



![](img/a136e4cb912e0823293b902b801b375f_1.png)

![](img/a136e4cb912e0823293b902b801b375f_2.png)

So penal demands we have to pay right will not gain but we will lose so instead of profit we are calling it as penalty so now the problem is to select the jobs and finish them within their deadlines such that the penalty is minimized。



![](img/a136e4cb912e0823293b902b801b375f_4.png)

![](img/a136e4cb912e0823293b902b801b375f_5.png)

Now if you are minimizing the penalty means automatically the profit is maximized。

 so just the name we have changed instead of profit we are calling it as penalty and one more thing here is these are the deadlines for each job and these are the times taken by each job。



![](img/a136e4cb912e0823293b902b801b375f_7.png)

![](img/a136e4cb912e0823293b902b801b375f_8.png)

![](img/a136e4cb912e0823293b902b801b375f_9.png)

The amount of time taken for completion of the jobs is varying it is not same one unit of time they are having different times I will solve it using branch and bound and the approach of solving is by generating a state space tree so we will be generating the nodes and for each node well define two values we will identify we compute two values that are cost and upper bound let us see what is upper bound and cost。



![](img/a136e4cb912e0823293b902b801b375f_11.png)

See upper bound for each note will be some of all the penalties。

Except those which are included in a solution so upper bound is some of all the penalties accept those which are included in a solution and the cost is some of all the penalties till the job that you have considered。



![](img/a136e4cb912e0823293b902b801b375f_13.png)

So cost is some of all the penalties still the last job that we have considered if S is the set of jobs that are included in a solution。

 then the upper bound is some of the penalties of all those jobs which are not in that set。



![](img/a136e4cb912e0823293b902b801b375f_15.png)

And the cost is the sum of all those jobs that are not in the set。Their penalties are added。

 and here we will consider up to the job that we have taken， so let us say K at the job。

 up to K at the job。So while solving， I will explain how these two are calculated。

 let us generate a state pastry。This is the first node。 and the cost is nothing。0。

 and the upper bound is infinity。

![](img/a136e4cb912e0823293b902b801b375f_17.png)

And here will maintain one value that is upper， and that is also will keep it as infinity。



![](img/a136e4cb912e0823293b902b801b375f_19.png)

Now one by one will consider the job first job let us say it is included in the solution， first job。

 if job one is included， then what is the cost if job one is included in the cost。

 then till job one you see so anything we are skipping nothing we are skipping so the cost is0 only。



![](img/a136e4cb912e0823293b902b801b375f_21.png)

Now， when first job is in the solution， remaining jobs penalties。 So that is 10 plus 6 plus 3。

 So penalties 10 plus 6 plus 3。

![](img/a136e4cb912e0823293b902b801b375f_23.png)

Is 19。So this is upper。

![](img/a136e4cb912e0823293b902b801b375f_25.png)

Now we got one upper value， which is less than that infinity， so update this one 19。Now， next job。

Job  one is over。 So job2， third node。 What is the cost See。

 this means that we are including second job。 So first job we are not doing。

 So what is the penalty of first job 5。

![](img/a136e4cb912e0823293b902b801b375f_27.png)

5， and what is upper。 So except second job， we have to take the penalties of all。

 So this is 5 plus 6 plus 3。

![](img/a136e4cb912e0823293b902b801b375f_29.png)

F plus 6 plus3 is 14， so this is updated to 14。 So if we are getting any new upper value which is smaller than that one。

 we will change it。

![](img/a136e4cb912e0823293b902b801b375f_31.png)

![](img/a136e4cb912e0823293b902b801b375f_32.png)

Now， the next node will consider third job。 That is job 3。

So here the cost so it means that we are just taking third job we are not doing first second and fourth job。

 so till third job if you consider till here only we should consider so how many job we are living that is five and 10 so five and 10 so that is 15。



![](img/a136e4cb912e0823293b902b801b375f_34.png)

![](img/a136e4cb912e0823293b902b801b375f_35.png)

![](img/a136e4cb912e0823293b902b801b375f_36.png)

![](img/a136e4cb912e0823293b902b801b375f_37.png)

Now， one more thing we learn， see what I was doing every node I was calculating cost and upper bound cost and upper bound。

 If the upper bound is smaller， I was changing that one。

 but one more thing you also have to do that is what is the cost now 15， what is the upper bound 14。

 So that upper bound shows that if we are getting some penalty at most we may be getting 14。

 but this cost has increased exceeded。 So kill this node。 So this node is killed。



![](img/a136e4cb912e0823293b902b801b375f_39.png)

Then， fifth node。This means only job 4。 So when you are doing only job 4。

 then all three jobs we are skipping。 So 5，10 and 6。 So this is 5 plus 10 plus 6， and this is 21。



![](img/a136e4cb912e0823293b902b801b375f_41.png)

![](img/a136e4cb912e0823293b902b801b375f_42.png)

![](img/a136e4cb912e0823293b902b801b375f_43.png)

Cost is higher than 14。 So kill this node。 No need of finding upper bound at all。

 I have only two live nodes， which are not killed。 Let us expand。 So this node， I will expand。

 So first job 1 was done， not job 2。 and Also， I should try job 3 and job 4。

 So Ill calculate them 1 by 1，6，7 and 8 node。 So what is the cost。

 see this means that we have included first job Also， second job also， So we are at second job。

 right， So is there anything that we are skipping node， what the jobs we are doing。

 So the cost will be 0。 And what will be the upper bound。

 upper bound is when we are doing first job and second job remaining is 9。

 So this is 9 upper bond is 9。 So we got it minimum value。 That is less than 14。 So update it to 9。



![](img/a136e4cb912e0823293b902b801b375f_45.png)

![](img/a136e4cb912e0823293b902b801b375f_46.png)

![](img/a136e4cb912e0823293b902b801b375f_47.png)

![](img/a136e4cb912e0823293b902b801b375f_48.png)

![](img/a136e4cb912e0823293b902b801b375f_49.png)

Then next cost of this one。 So the cost of this one is。

This means that first job and third job we are doing。

 we are not doing second job that is penalty is a 10， so cost is 10 and what is upper9 kilos node。



![](img/a136e4cb912e0823293b902b801b375f_51.png)

![](img/a136e4cb912e0823293b902b801b375f_52.png)

Then cause of the snored。J is 4， J 1， J 4。 So J 1 and J 4。 So we are not not doing J 2 and J 3。

 That is 16。 So the cost is 16。 Kill this node。

![](img/a136e4cb912e0823293b902b801b375f_54.png)

![](img/a136e4cb912e0823293b902b801b375f_55.png)

That is greater than nine。Now which node we should explore second node we have already explored。

 let us explore third node。

![](img/a136e4cb912e0823293b902b801b375f_57.png)

Now third node， this is ninth node。 So this is job 2， so we can do job 3 and job 4。10th note。

 Let me calculate the cost。 See， the cost of this one is。This is second job and third job。

 So we are doing second job and third job， which job we are not doing， first job we are not doing。

 so the cost will be 5。

![](img/a136e4cb912e0823293b902b801b375f_59.png)

Is it less than 9。 Yes， then what is upper bound， I will calculate upper bound also。 So out of all。

 we are doing second job and third job， remaining job。 So that is first and fourth。

 So that is 5 plus 3。 It is 8。 Oh， we got a minimum value。 updated to 8。



![](img/a136e4cb912e0823293b902b801b375f_61.png)

![](img/a136e4cb912e0823293b902b801b375f_62.png)

A10 node cost。 See， this is second job and food job we are doing。

 So we are not doing faster giant third job， right， we are on the fourth job。 so this is 11。

 So this is 5 plus 6。 That is 11。 and the 11 is greater than 8。 So kill this node。



![](img/a136e4cb912e0823293b902b801b375f_64.png)

![](img/a136e4cb912e0823293b902b801b375f_65.png)

![](img/a136e4cb912e0823293b902b801b375f_66.png)

Next one， which we should explore this one。 So this one， if it is explored， then this is job tree。

See here， the problem solving is Ly。 So I am showing you what are the things you should do in steps。

 Now， at this stage， I can explain you that you have to consider one more thing while doing all these that we did not do。

 Now we need it。 What is that doing job 1 and job 2， as well as job 3 is it possible or not。

 Jo  ones deadline is one。 Okay， that isn in first start。 and job  twos deadline is3。 Okay。

 it will wait till third R then job 3 is deadline is 2。 Jo 3 deadline is 2。 So let us check them。



![](img/a136e4cb912e0823293b902b801b375f_68.png)

![](img/a136e4cb912e0823293b902b801b375f_69.png)

Job 1 deadline is one。 Jo2， deadline is a3， and job 3 is deadline is one。

And what are the processing time，1 plus 2 plus1。 See， if I complete these two together。

 then the total time taken will be three。 Tot time will be taken 3。

 This job doesn't require one hour， it requires two hours。 So first star will do this。

 and remaining two hours。 This job can be done。 So there is no time left for doing this job。

 So it means when you have taken first job and second job。

 Third job cannot be done based on their time， not based on the deadline based on the time。

 because this needs two hours。 So this job cannot be done， So need not generate this note。

 Next fourth job， fourth job also the same case。 it also need one time。 So this cannot be done。 Now。

 which is the last live nor remaining。 This is skill。 This is skill this one。

 So let us expand this one。 So what I can take here。 Jo 2， job 3， Jo 4。 Can we do job 4。

 Let us check， See job。

![](img/a136e4cb912e0823293b902b801b375f_71.png)

![](img/a136e4cb912e0823293b902b801b375f_72.png)

2 is done。 That needs。2 units of time and deadline is3， and the job 3。 Its deadline is2。

 and it needs one unit of time， so they can finish off in three hours。 Now。

 fourth job it needs one extra time。 So this cannot be done。 So this is also infeible and pitol。

 This is inible。 We have finished the entire three。

 Then what is the minimum penalty or what is the minimum cost we got， That is 8 and 5。

 This is the node。 So the cost that we got is 5 and the penalty is got as 8。

 What are the jobs that we'll be doing。 Jo 2 and job 3。



![](img/a136e4cb912e0823293b902b801b375f_74.png)

![](img/a136e4cb912e0823293b902b801b375f_75.png)

Job 2 and job 3 so。If we complete job 2 and job 3， then the penalties that we will be saving are 10 and 6 that is 16 and how much penalty we have to pay Jo 1 and job4 are not done。

 So their penalties are 5 and3， so that is 8。 so the penalty that will be paying us8。



![](img/a136e4cb912e0823293b902b801b375f_77.png)

So that's how we got the solution。
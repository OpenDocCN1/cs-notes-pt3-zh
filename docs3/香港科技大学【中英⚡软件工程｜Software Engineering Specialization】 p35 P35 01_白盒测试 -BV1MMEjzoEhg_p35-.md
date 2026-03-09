# 香港科技大学【中英⚡软件工程｜Software Engineering Specialization】 p35 P35 01_白盒测试 -BV1MMEjzoEhg_p35-

Hi this is the second lecture about testing in this lecture we will talk about the three types of tests that we can perform on a software system and they are white box testing。

 black box testing and also we question testing。And we will start with white box testing and in the last lecture we have already covered what is basic path testing and in this lecture we will focus on conditional testing。

 loop testing and also data flow testing So of you may ask why do we want to perform conditional testing on conditional statements that we have within a program and the reason is that it's easy to make mistakes on conditional statements and that's why we want to focus testing on those statements that we can easily make mistakes on and in conditional testing we try to execute the true and false values of each simple logical condition in a component and we focus on conditional statements that we have within a program for example。

 a simple condition compound condition relational expression or boolean expression and again we want to focus on testing conditional statements because they are the places that we can easily make mistakes due to incorrect missing or extra boolean operator Boolean verbal furnas relational operator。



![](img/db0321bcb43a29178586b12db537a991_1.png)

![](img/db0321bcb43a29178586b12db537a991_2.png)

![](img/db0321bcb43a29178586b12db537a991_3.png)

Or arithmetic expression。 And if we have a compound statement within our program， for example。

 some condition and another condition， then we should test every simple condition that we have within the compound statement。

 and notice that basic path testing already covered this cases。 Now， let's take a look at an example。

 Now， let's say we have a compound statement within our program。 For example。

 statement number 6 is a compound statement。 and we have like if a。



![](img/db0321bcb43a29178586b12db537a991_5.png)

![](img/db0321bcb43a29178586b12db537a991_6.png)

And B。Then we perform sta number seven， and then else we're going to perform something else。



![](img/db0321bcb43a29178586b12db537a991_8.png)

And now let's say we have this program and we want to derive the photograph for this program。

What we're going to do is that we're going to separate the compound statement into two simple conditions。

 which are 6 a。

![](img/db0321bcb43a29178586b12db537a991_10.png)

![](img/db0321bcb43a29178586b12db537a991_11.png)

For the condition A， and then 6 B。For the condition B。Now， once we execute statement number six。

 we going to first double check the condition 6 a。If 6， a is true。What are we going to do。

We can double check the condition for 6 B。Okay， then if 6 B is also true， what we good to do？



![](img/db0321bcb43a29178586b12db537a991_13.png)

So both 6 A and 6B， they are true。 That means the entire compound statement is going to be true。



![](img/db0321bcb43a29178586b12db537a991_15.png)

So we are going to execute statement number seven。What if 6， a is false。



![](img/db0321bcb43a29178586b12db537a991_17.png)

Then we're going to execute the L statement。We use statement number a。



![](img/db0321bcb43a29178586b12db537a991_19.png)

What if 6 a is true and then 6 B is false。

![](img/db0321bcb43a29178586b12db537a991_21.png)

Then again， we go to the out statement because it's going to make the compound statement false。

 So that's why we go into the else statement。 So if you have a compound condition in your program。

 then eventually you will have a triangle like this。

In your flow graph and you're going to double check all the simple conditions that you have within your flow graph using basic path testing and all the simple conditions that we have within the compound statement will be covered by basic path testing because we treat each simple condition separately。



![](img/db0321bcb43a29178586b12db537a991_23.png)

And then we will also perform domain testing。 For example。

 let's say we have E1 is going to be bigger than E2。 Let's say x is bigger than4。In our program。

 then we do something。Then what we're going to do is that we have to test the statement using values that is going to make E1 greater than E2 E1 equal to E2 and E1 less than e2 and let's say we want to double check whether x is bigger than4 in our conditional statement then we need some x which is less than4 for example2 and we need some x which is equals to 4 and then also we need some x which is bigger than4 for example6 to test out the conditional statement so in this case we need three inputs。

To test out the conditional statement， for example， exit bigger than4。 Then for loop testing。

 we focus on testing， executes loops at and within their bounds。 For example。

 you know that in a loop， you're going to have an iterations。



![](img/db0321bcb43a29178586b12db537a991_25.png)

Then what you need to test is that you need to test the loop with01 or two passes or M passes where M is less than n。

And then n minus-1 n and n plus 1 passes through the loop。

Just to make sure that the loop is going to work well at the minimum number of passes at the maximum number of passes and also some normal number of passes within the range。

 Now， if we have nested loop， then we're going to conduct simple loop test for the innermost loop while holding the outer loop at their minimum iteration values。

 That means for the inner loop， we're going to apply simple loop testing。

 that means we have to test the loop using01 and 2 passes M passes and also n minus1 n and n plus one passes。



![](img/db0321bcb43a29178586b12db537a991_27.png)

And then for the outer loop， we keep it at its minimum iteration values， for example。

 just zero or one passes。Why do we do that， We want to focus on， for example。

 testing the inner loop while making the outer loop simple。Okay。

 then the next thing that you should do is to work outward。 Okay。

 that means you're gonna to make the inner loop simple with0 or one passes。

And then apply simple loop testing on the outer loop and then you will continue on until all the loops they have been tested and notice that tests grow geometrically with level of lasting。

 So that means if you have one loop within another loop within another loop within another loop you will need more time for testing and what if we have like concatenated loops。

 that means one loop followed by the other。

![](img/db0321bcb43a29178586b12db537a991_29.png)

If the two loops right they don't depend on each other then we can apply simple loop testing on each of them if they are dependent on each other。

 then you can apply nest loop testing that means you test one of the loop while making the other loop at this minimum number passes and what if we have like unstructured loops in our program and notice that we should not have any unstructured loops in our program if they exist right then you should befactor the code and then improve the structure of your source code。



![](img/db0321bcb43a29178586b12db537a991_31.png)

![](img/db0321bcb43a29178586b12db537a991_32.png)

So that's the route that we want to keep in now mind。

 We want to come up with some tests that have the highest chance of uncovering errors with the minimum ethics。



![](img/db0321bcb43a29178586b12db537a991_34.png)

And another type of white box testing that we can perform on a program is data flow testing in data flow testing。

 we try to ensure that the value of a variable is correct at certain points of execution in the code。

 So what is a de use chain， for example， if you have a variable x。

 then the de use chain of x It's going be the place that you define x。

Up to the point where you use or consume eggs。So in data of flow testing。

 we focus on the path where we define x and then later on where we use x and we focus on those paths and then in our program every depth use chain must be covered at least once。



![](img/db0321bcb43a29178586b12db537a991_36.png)

And for every rever， do a test along the path from where the variable is defined to the statements where the variable is used。



![](img/db0321bcb43a29178586b12db537a991_38.png)

In this test， they can be combined with basic path testing。


# 香港科技大学【中英⚡软件工程｜Software Engineering Specialization】 p34 P34 03_基本路径测试 -BV1MMEjzoEhg_p34-

And now in basic path testing， we try to execute all the independent paths that we have within the program at least once。

And what we're going to do is that we're going to derive a logical complexity measure in terms of psychomatic complexity for the code and then use this measure to define a basic set of execution paths。

 a set of independent paths that we're going to use for testing。

So what we're going to do is that from the code we're going to draw a flow graph and then we're going to determine the psychometric complexity from the flow graph。

 and then after that we're going to determine a set of linearly independent paths based on the psychometric complexity。

And then finally， we're going to prepare a set of test cases that we' execute。And then finally。

 we will prepare a set of test cases that will first execute the independent paths that we have in the basic set。



![](img/b2a63f9310fbae644c975e13cbce1f6d_1.png)

So the first thing that we have to do is to draw a flow graph。

 and these are the notations that we can use in a flow graph。

If this sequential execution of statements one by one， we can use this drawing。 Okay。

 one statement after the other。If we have a conditional statement， then we can use this drawing。

If the condition is true， we do something。 Otherwise， we do something else， et cetera， et cetera。

 If we have case or switch， then we can use this drawing。 Okay， we have different conditions。

If we have a do while loop， then we're going to draw this， okay。

 do something while something is true until the condition is not true。

 then we're going to exit the loop。Or do until loop， okay， do something。

Until the condition is no longer true， then we exit the loop。



![](img/b2a63f9310fbae644c975e13cbce1f6d_3.png)

So now let's try to draw a throw graph for this little procedure。



![](img/b2a63f9310fbae644c975e13cbce1f6d_5.png)

So now we start with statement number one， which is a duval loop。 And if the condition is true。

We're going to continue with statement number two and also statement number three。

And then statement number three is a conditional statement。



![](img/b2a63f9310fbae644c975e13cbce1f6d_7.png)

If it's true， then we're going to execute sta number four and five。Okay， if it's false。

 then we can execute Damen 6 and 7。

![](img/b2a63f9310fbae644c975e13cbce1f6d_9.png)

And now you can see that statement number  seven is another conditional statement。 if it's true。

 then we can execute statement number8， if it's false。

 then we can execute statement number  nine and also number 10。



![](img/b2a63f9310fbae644c975e13cbce1f6d_11.png)

![](img/b2a63f9310fbae644c975e13cbce1f6d_12.png)

![](img/b2a63f9310fbae644c975e13cbce1f6d_13.png)

In sequence。And then finally， after we finish the if statement。

 we're going to merge them into note number 11， which is N if。



![](img/b2a63f9310fbae644c975e13cbce1f6d_15.png)

And then M order statement4 N if。

![](img/b2a63f9310fbae644c975e13cbce1f6d_17.png)

And then finally， an another statement for and do。

![](img/b2a63f9310fbae644c975e13cbce1f6d_19.png)

Okay， then we go back to the do while loop and then do the check in again。



![](img/b2a63f9310fbae644c975e13cbce1f6d_21.png)

And then we're going to check the condition again for this dual value loop if the condition is true。

 we're going to execute statement number  two，3， etc cetera， etc cetera。 If it's false。

 then we end the program and then we go to statement number 14。And then after you get the flow graph。

 the next thing that you have to is to simplify the flow graph by combining those sequential statements together。

So in this example， we can see that no matter what we're going execute， for example。

 statement number two and number three together， then we can combine them together as once go node。

And also we will see that no matter what we have to execute， for example。

 statementmen 4 and5 together and also stamen 6 and 7 together and also sta 9 and 10 together and then 12 and 13 together。

 so now we can combine them together as a single node。



![](img/b2a63f9310fbae644c975e13cbce1f6d_23.png)

![](img/b2a63f9310fbae644c975e13cbce1f6d_24.png)

![](img/b2a63f9310fbae644c975e13cbce1f6d_25.png)

And there are some rules that we can use for combining sequentialncial statements together as a single note。

 we can start with a simple note。

![](img/b2a63f9310fbae644c975e13cbce1f6d_27.png)

![](img/b2a63f9310fbae644c975e13cbce1f6d_28.png)

And what is the definition of a simple note right， S note is going to be just a note with one single outgoing arrow Okay。

 so now we can see that for statement number two， we only have one outgoing arrow。

 so it's going to be a simple note。

![](img/b2a63f9310fbae644c975e13cbce1f6d_30.png)

![](img/b2a63f9310fbae644c975e13cbce1f6d_31.png)

![](img/b2a63f9310fbae644c975e13cbce1f6d_32.png)

What if we have more than one outgoing arrows， for example， statement number3。

 which can be either true or false， then we have a predicate。



![](img/b2a63f9310fbae644c975e13cbce1f6d_34.png)

No， so now one rule that we can use for merging sequential statements together as a single note is that we can start with a simple note。

 which is this one。

![](img/b2a63f9310fbae644c975e13cbce1f6d_36.png)

Until we see a predicate no。And then we also include the predcate note into the groupoove。

So as another example， statement number six is another simple no。

 and then we keep merging until we see a predicate no。



![](img/b2a63f9310fbae644c975e13cbce1f6d_38.png)

诶。

![](img/b2a63f9310fbae644c975e13cbce1f6d_40.png)

Or another route that we can use is that we start with a simple one。

 and then we keep merging until we see a。No， for example， statement number 12， which is shared。

By two paths， okay， this is like path number one， and this is path number two。

This note is shared by two paths。Okay， then。What we're going to do is that we start with a simple note until we see a null which is shared by two paths。

 and then we don't include this channel into the group。 So that's why in this group we only have。

 for example， statement 4 and5 together。But not stay 12 because we don't include the shared no into the group。

And then this is in our example， we start with a simple note which is statement number nine and then we merge until we see 11 which is shared。

And then we stop and we don't include 11 into the group。

So these are some of the rules that you can use for merging sequentialncial statements together as a group。



![](img/b2a63f9310fbae644c975e13cbce1f6d_42.png)

And after simplification， this is the f graph that we're going to get。

And after we group the sequentialial statements together as a single note。



![](img/b2a63f9310fbae644c975e13cbce1f6d_44.png)

This is the simplified version of the photograph graph。

And after we get the simplified version of the photograph， don't forget about this mapping table。

Don't forget about this mapping table because it's going to tell us， for example。

 for note number two， we are referring to statement 2 and3 because in our original program。

 we can see that this group is actually for statement 2 and3。

 so that's why when you draw a photograph you need this simplified version of the F together with a mapping table to tell us exactly for example。

 a note is going to map to which statements in our program。



![](img/b2a63f9310fbae644c975e13cbce1f6d_46.png)

![](img/b2a63f9310fbae644c975e13cbce1f6d_47.png)

![](img/b2a63f9310fbae644c975e13cbce1f6d_48.png)

And then after you get the flow graph， you have to determine the psychometric complexity of the flow graph and the psychometric complexity。

 which is denoted as v of G。It's going to be a quantitative measure of the logical complexity of the source code。

 So if your source code is logically complicated。Pyromatic complexity will go higher。

Just because you have so many independent paths within your program。

And psychometric complexity is going to provide an upper bound on the number of paths that needs to be tested in the code。

 So it's just an upper bound， maybe less than that。So how to calculate psychometric complexity。

 there are a few ways that we can use for calculating psychometric complexity。

 the first one is to count how many regions that we have within the flow graph。



![](img/b2a63f9310fbae644c975e13cbce1f6d_50.png)

So now let's consider putting different colors onto different regions on this program。

 then we can put one color on region one and then another color on region number two and then another color on region number three and don't forget about the outside region。

And which is like the background region， which is region number four。

 So if we are considering like coloring this photograph， then we have four different regions。



![](img/b2a63f9310fbae644c975e13cbce1f6d_52.png)

Then the psychometric complexity of this photograph is going to be4。😡，Or you can also use。

 for example the number of edges minus the number of nodes plus2 If you count carefully you will find that we have 11 edges and  nine nodes within this full graph。

 so using this equation number of edges minus number of nodes plus 2。

 you get the same psychometric complexity which is 4 or you can count the number of predicate nodes plus 1。



![](img/b2a63f9310fbae644c975e13cbce1f6d_54.png)

![](img/b2a63f9310fbae644c975e13cbce1f6d_55.png)

![](img/b2a63f9310fbae644c975e13cbce1f6d_56.png)

So in this program， we have Note one as a predicate note because it has like two branches going out。

And then note number two is also a predicate note。Note number four is also another pre because it has branches。

So now you can see that in this photograph we have three preddiiccate nodes and then using the equation that means the number of prediiccate nodes plus one。

 we're going to get the same psychometric complexity which is four。



![](img/b2a63f9310fbae644c975e13cbce1f6d_58.png)

![](img/b2a63f9310fbae644c975e13cbce1f6d_59.png)

AndNow we can see that for this particular flow graph， V or G。

 the psychometric complexity is going to be4 and that means the upper bound of the number of independent paths that we can have for this flow graph is going to be4 and then after we determine the psychometric complexity we have to determine a basic set of linearly independent paths from the flow graph and the definition of independent path is a path that introduces at least one new set of processing statements or a new condition。



![](img/b2a63f9310fbae644c975e13cbce1f6d_61.png)

And an independent path must traverse at least one edge in the flow graph that has not been traversed before the path is defined。

 and a basic set is the set of linearly independent paths through the code。

 And notice that a basic set is not unique。 That means you may have more than one set of independent paths from the same code。

 And test cases derived it from a basic set are guaranteed to execute every statement at least once。

During testing that means using basic path testing is going to guarantee that every single statement that you have in the program is going to be executed in the test。

 So now let's take a look at this example and we can see that we have three regions in this f and the psychometric complexity is free And now the question is that how many independent paths that we have in the basic set and remember that an independent path introduces at least one new set of statements or a new condition that means it traverses at least one new edge in the F。



![](img/b2a63f9310fbae644c975e13cbce1f6d_63.png)

![](img/b2a63f9310fbae644c975e13cbce1f6d_64.png)

And the answer is2 again， the basic set may not be unique。

 so that means we're going have more than one basic sets for the same code and for the same flow graph and notice that the number of independent paths that we have in a basic sets is smaller than the psychometric complexity because the psychometric complexity is going to be just an upper bound on the number of independent paths that we have for a flow graph So the number of independent paths that we have in a flow graph may be less than the psychometric complexity。



![](img/b2a63f9310fbae644c975e13cbce1f6d_66.png)

So in the first basic set， we have one path and then we have an other path which is independent to the red one and then in the second basic set。

 we have one path， which is the red one and then we have an another path which is the green one which is independent to the red one So when we perform testing。

 we can choose to either use the first set or the second set And in this example。

 the basic set is not unique and also the number of paths that we have in the basic set is less than the psychometric complexity again。

 just because the psychometric complexities and upper bound on the number of independent paths that we have for a given photograph graph。



![](img/b2a63f9310fbae644c975e13cbce1f6d_68.png)

![](img/b2a63f9310fbae644c975e13cbce1f6d_69.png)

![](img/b2a63f9310fbae644c975e13cbce1f6d_70.png)

So in this example that we have seen before， since the psychometric complexity is4。

 that means we're going to have at most four independent paths in the basic set。

And these are the independent paths that we have in this f graph。

Wehich is like from statement 1 to 14。Stment 1，2，3，4，5， 12， 14 and M 14。And then 1，2，3，67，8， 11，12。

13 and 14， and then last one is 1，2，3，6，7，9， 10， 11， 1213 and then 14。

 but notice that this path one and then 14 is not really independent to the other paths because you can see that one and 14 already exist in the other paths。

But still it's a good idea， even though it's not an independent path。

 it's a good idea to test out this path when we perform testing， why？



![](img/b2a63f9310fbae644c975e13cbce1f6d_72.png)

So remember that the first statement is a do while statement。So what if。

So remember that the first statement is a dowhile kind of statement。

 so while we have rackets in for example， an array。

 then we're going to perform something otherwise we're going to exit the program。

And when we perform testing， it's a good idea that we're going to try it out， for example。

 the program with an array which is empty without any record。For example。

 if there's no record in the array， then I'm going to exit the program immediately。

 which is like going from statement number  one and then 14。



![](img/b2a63f9310fbae644c975e13cbce1f6d_74.png)

So that's why even this path 1 and M 14 is not independent to the other paths。

 it's a good idea to include it in our testing because it's going to test out the situation when the array is empty and we don't have any record。

 then we can exit the program immediately。

![](img/b2a63f9310fbae644c975e13cbce1f6d_76.png)

And then after we get all the independent paths from our basic set。

 we're gonna to prepare the test cases that force the execution of each path in the basic set and notice that the basic set refers to the statement numbers in the program for example in this example for that we have each path is going to be just a set of statements and then we also have to count each logical tasks to make sure that we have cover all the predcate notes。

 all the conditional statements or statements with branches in our flow graph and then finally basic path testing should be applied to all components if possible。



![](img/b2a63f9310fbae644c975e13cbce1f6d_78.png)

![](img/b2a63f9310fbae644c975e13cbce1f6d_79.png)

And two critical components always。 So some of you may ask。

 do we applied basic path testing to every single procedure that I have within my program。

 I will say no， because drawing flow graph is going to take time。

And if you have many many procedures within your program。

 this' is going to take a long time to finish all the basic path testings within your program。

So that's why I say that when we perform basic craft testing。

 we focus on critical components that are logically complicated， for example。

 if you have a procedure with many， many conditional statements and also many。

 many loops and its logically complicated then we should apply basic craft testing on that particular procedure。

 but let's say if you simply have a procedure which is like sequential execution of a set of statements。

Then you may skip basic path testing on that procedure because it's not logically complicated。

 but notice that in basic path testing， we do not test all the possible combinations of all the paths through the code。



![](img/b2a63f9310fbae644c975e13cbce1f6d_81.png)

But instead， we simply test every path that we have in the flow graph at least once。



![](img/b2a63f9310fbae644c975e13cbce1f6d_83.png)

And that's all I wantan to cover in this lecture。
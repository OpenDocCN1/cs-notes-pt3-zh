# 【精译⚡算法导论】AbdulBari p66 p65 6.3 Graph Coloring Problem - Backtracking -BV1hhPXeTEWM_p66-

The topic is graph coloring problem。 This can be solved using back trackinging。 First of all。

 let us know what the problem is。

![](img/a154013540988b66b2f0288710fa1a86_1.png)

See a graph as given。

![](img/a154013540988b66b2f0288710fa1a86_3.png)

And some colors are given。 Let us say3 colors are given。 That is red， green and blue。

NowThe problem is we have to color the verortices of a graph such that no two neighboring verortices or adjacent vertices must have same color。

So three colour are given to me。 Let us try and see what colorss we can give。

 whether it is possible or not possible。 So I'll start from vertex 1。

 I'll give red color to this one。Now I'll pick up second vertex2 who are neighboring to2，1 and3。

 but already red color is there to this neighboring vertex so this two cannot take red color so okay we'll give green color。



![](img/a154013540988b66b2f0288710fa1a86_5.png)

Now go to what X 3， Which color I can give。 Can I give red color， It's not adjacent to one， Yes。

 I can take red color。 Then what X 4， can I give red color， This is adjacent to this one。 No。

 can I give green color， So is it adjacent， I it adjacent。 No， I can take this color。Then here。

 can I give red color。 No， this is adjacent to this one。 Can I give green color。

 This is adjacent to this， So I cannot take green color。 Can I take blue color。 Yes。

 this is not green， This is not。 So it's different from all three。 So I can take blue color。

 So I have vertics 1，2，3，4 and 5。 and the colors is what I have now as red， green， red。

 green and blue。

![](img/a154013540988b66b2f0288710fa1a86_7.png)

![](img/a154013540988b66b2f0288710fa1a86_8.png)

Yes， a graph can be colored like this。Is it the only solution or there are other solutions possible。

 Yes， I can colour it in a different way。 Also， let us see。 instead of red color。

 I'll give green color here。And here I cannot take green。 So I take red here。 And here。

 I cannot take a red。 So I'll take green。 And instead of green。 I'll give you a red color。

 And this is blue。 Okay， I'll give blue only for this one。 See， for the other vertices。

 The colors has changed。 It means that same vertices can be color in different ways。

 So there are more than one solutions possible and here we want all possible solution。

 What are the ways they can be colored。 So it is like permutation or trying out all possibilities and then picking up the one which are satisfying the condition。

 What is the condition neighboring vertices should not have same color。 So， yes。

 this type of problem can be solved using backtracking。

 When you want multiple solutions and there is a different possible solution， go for backtracking。

 here we learn two things。 See， three colors were given to us and we have colored。 the graph。

 If I give just two colour， I don't give blue color。 Can the graph be colored in this one， No。😊。

It cannot be colored。So if I give four colors， one more color， yellow。

 can the graph be colored and that is， it can be colored。So we will define one type of problem here。

If a graph is given and some colors are also given and just we want to know whether a graph can be colored by using those colors or not。

 we don't want the colors， We don't want the colors of the vertices。

 just we want to know it can be colored or not， So this problem is called as M coloring decision problem it is M coloring。



![](img/a154013540988b66b2f0288710fa1a86_10.png)

![](img/a154013540988b66b2f0288710fa1a86_11.png)

M coloring decision problem。We'll define one more problem here if a graph is given and we want to know minimum how many colors required for coloring the graph。

 and this problem is called as M coloring optimization problem。



![](img/a154013540988b66b2f0288710fa1a86_13.png)

M coloring。Optimization problem。

![](img/a154013540988b66b2f0288710fa1a86_15.png)

Now， we can say there are three type of problems。 One is if a graph is given and the colors are given。

 we want to know in how many ways the vertices can be colored。 what are the possible colors。

 This is one type of problem。 Second thing is colors are given。

 Just we want to know whether the graph can be colored with those vertices or not。

 And the third thing is colors are not given。 Just we want to know minimum how many colors are required for coloring this graph。

So before start coloring， first of all we we need to know minimum how many colors we should have。

 so for that we go for optimization problem。

![](img/a154013540988b66b2f0288710fa1a86_17.png)

Right， or else we already have some colors。 and we want to know whether these colors will be sufficient to color this graph or not。

 So then this is problem。

![](img/a154013540988b66b2f0288710fa1a86_19.png)

And coloring decision problem。 This is also called as chromatic number problem。

 chromatic number problem。 Col is m coloring is chromatic number。

 So decision problem or optimization problem。 Now we take a simple graph and show you how this can be solved using backtracking。

 Here is a simple graph and three colors are given。

 I have to color those vertices such that no two adjacent vertices are having same color。

 So this problem can be solved using backtracking。 And the method of solving a problem in backtracking is by generating a state spacee tree。

 So first I will generate the state space tree without any conditions or any checkings。

 I will simply generate a state spacee tree。 So let' us take， this is the root vertex。 Then first。

 I will consider the first vertex vertex 1。 So this is for vertex 1。 So I can call it as x1。

 So for this， I can give either red color or green color or blue color。



![](img/a154013540988b66b2f0288710fa1a86_21.png)

And second vertex， second level， second vertex can have either red color or green color or blue color。

 then here also red color green。Or blue。

![](img/a154013540988b66b2f0288710fa1a86_23.png)

Red。Green。And blue。Then under this， this is for the third vertex。Third vertex， red color。



![](img/a154013540988b66b2f0288710fa1a86_25.png)

![](img/a154013540988b66b2f0288710fa1a86_26.png)

So I have filled all possibilities for third vertex， now I will fill for fourth vertex。



![](img/a154013540988b66b2f0288710fa1a86_28.png)

![](img/a154013540988b66b2f0288710fa1a86_29.png)

Now this tree is showing all possibilities in which I can color them without checking the adjacency condition without checking any condition means the neighboring vertices can have same color also。

 So this is the possibility。 So I have drawn a big graph it becomes very big。

 if you don't apply any condition。 but in backtracking。

 we impose conditions and solve the problem right， but without any conditions， if I generate。

 let us check total how many nodes are generated， that is root is having fast node。

 then first level is having three nodes。

![](img/a154013540988b66b2f0288710fa1a86_31.png)

Second level is having three into3 nodes。Then third level is having three into three into three nodes that is 27 nodes。

 3 into3 into3，27， and the next level is having three into three into three into three nodes。



![](img/a154013540988b66b2f0288710fa1a86_33.png)

![](img/a154013540988b66b2f0288710fa1a86_34.png)

See， these many nodes are generated without imposing any bounding function or condition。

 Then how many nodes are these。

![](img/a154013540988b66b2f0288710fa1a86_36.png)

Right， this is。This is  one plus 3 plus 3 square plus 3 Q plus 3 power 4。 So for four vertices。

 it is forming3 power 4。 So this is。

![](img/a154013540988b66b2f0288710fa1a86_38.png)

![](img/a154013540988b66b2f0288710fa1a86_39.png)

3 to the power of 4 plus 1-1 by 3-1。 So this is 3 power4 plus 1-1 by 2。

So this is approximately three power n plus 1 and is the number of what it says。 And what is3 here。

 C， C to the power of n plus 1。 So the time complexity for generating these means time is nothing but the number of nodes you are generating for each node you consider this one unit of time。

 So total time span is。

![](img/a154013540988b66b2f0288710fa1a86_41.png)

3 power N or C power N。 So this is exponential time taking problem。 Now。

 let me solve it using back trackinging。 So we imagine that all these nodes are generated。

 but back trackinging will reduce it。 So still， we consider the time is this much only。

I will solve this using backtracking by also checking bonding function let us start I'll generate a state space 3。

 Now this is the first vertex vertex 1 Im calling it as x1 so for this I can give it correct color。等。

Next vertex is x2。

![](img/a154013540988b66b2f0288710fa1a86_43.png)

Now， once for vertex 1 has red colour， can I give red colour to this one， No， they are re。

 So red color cannot be given。 So if I use red color。

 then this node is a killed by bounding function。 So this is killed。



![](img/a154013540988b66b2f0288710fa1a86_45.png)

Now， I can give another color。 Let us take a green color here。 So， yes， green color is allowed。

 So I'll take a green color here。 So the next vertex is green color。 See for the second vertex。

 color is green。 Yes， this is valid。 Now， once you've got a valid color， go to the next vertex。

 that is third vertex。😊。

![](img/a154013540988b66b2f0288710fa1a86_47.png)

![](img/a154013540988b66b2f0288710fa1a86_48.png)

So to the third vertex， third vertex， can I give red color， check it here。 Yes。

 this is not adjacent to one。 It's adjacent to2， and they are having different color。 Yes。

 this is allowed。 Now， once I got a valid color， I'll move to next vertex。 that is vertex 4。



![](img/a154013540988b66b2f0288710fa1a86_50.png)

![](img/a154013540988b66b2f0288710fa1a86_51.png)

So let us check first。 Can I give red color。 So here， red color。 No red color。 This is adjacent to 2。

 so it cannot be given。 So this node is killed by bonding function。 Let me try next color。

 That is green。 Can I give green color。

![](img/a154013540988b66b2f0288710fa1a86_53.png)

![](img/a154013540988b66b2f0288710fa1a86_54.png)

![](img/a154013540988b66b2f0288710fa1a86_55.png)

Yes， it can be given and this is different from these two yes， the green color can be given。



![](img/a154013540988b66b2f0288710fa1a86_57.png)

Now see it is like depth for search。 We are at this stage。

 so now next I should try another color also that is blue color， Can I give blue color to this one。

 Yes， I can give blue color also so these are two solutions see red green。

 red and green blue green also and blue also so I have two solutions like this。



![](img/a154013540988b66b2f0288710fa1a86_59.png)

![](img/a154013540988b66b2f0288710fa1a86_60.png)

![](img/a154013540988b66b2f0288710fa1a86_61.png)

First solution is red， green， red and green。 Second solution is red， green， and red， blue。



![](img/a154013540988b66b2f0288710fa1a86_63.png)

So I have tried all possible colors for fourth vertex。

 go back and try the next color for third vertex， red is given， now green。

 so I'll remove fourth vertex and here I'll mention green color。



![](img/a154013540988b66b2f0288710fa1a86_65.png)

![](img/a154013540988b66b2f0288710fa1a86_66.png)

Can it be given。 No， these are adjacent， So color cannot be given。

 So this is killed with bounding function。 Now， can I give blue color to this one。

 Let me try blue color。 Yes， blue color can be given。 Now， next fourth vertex again， fourth vertex。

 red color， red color for this one。 No， this is adjacent。 So this is killed by bounding function。

 Then green color。 Can I give green color here。

![](img/a154013540988b66b2f0288710fa1a86_68.png)

![](img/a154013540988b66b2f0288710fa1a86_69.png)

Yes， it can be given。 So this is a valid answer。 So red， green， blue， green。

 third answer I got is red， green， blue， green。

![](img/a154013540988b66b2f0288710fa1a86_71.png)

![](img/a154013540988b66b2f0288710fa1a86_72.png)

Now， I should try all colors。 Let me try。Blue colour here。 blue color。 This is a。 No。

 this node will be killed by bonding function。 So I have tried all possible colors for fourth vertex。

 Now， go back， third vertex， All three colour tried。 Now， go back to second vertex。

 So remove this color and this color。 Now， second vertex。 Second vertex green already。 we tried。

 Let us try with blue。 Can we give blue color to this one。 Yes。😊。



![](img/a154013540988b66b2f0288710fa1a86_74.png)

![](img/a154013540988b66b2f0288710fa1a86_75.png)

Now， next vertex， try red color for the third vertex。 Can it be given。 Let us check。 Yes。

 the adjacent vertex is that one， too， and it is not having red colour is valid。 Then try44 vertex。

 Can I give red color here。 Red color。 No， this is killed with bounding function。



![](img/a154013540988b66b2f0288710fa1a86_77.png)

![](img/a154013540988b66b2f0288710fa1a86_78.png)

![](img/a154013540988b66b2f0288710fa1a86_79.png)

Then green color can I give。

![](img/a154013540988b66b2f0288710fa1a86_81.png)

Yes， adjacent vertices are red， so this can be given。 So I have one more solution now that is R， B。

 R， G。

![](img/a154013540988b66b2f0288710fa1a86_83.png)

![](img/a154013540988b66b2f0288710fa1a86_84.png)

NowFor the fourth word， X I tri color blue， Yes， blue can also be given。 It's adjacent vertices。

 so not having that color。 So R B， R B is one more solution。 That is R B， R， B。



![](img/a154013540988b66b2f0288710fa1a86_86.png)

![](img/a154013540988b66b2f0288710fa1a86_87.png)

Then go back for the third vertex。 Now in this way I can continue and and find out all possible solution。

 See by applying bonding functions， some of the nodes are getting killed。

 So at most it' is going to be3 power n。 Finally， So we say that the time complexity for solving this is3 power n。

 Now let me show you where the graph coloring problem is useful。

Now let us see where this graph coloring problem is useful。

 so here I have a map and the map is having different regions。

 Supp I have to color this map such that no two adjacent regions are having same color。

Why I want to know this， See， The reason is in olden days when the printing was done for each colour。

The paper has to be passed through the printing press for one time。 So for N colors。

 it should be passed for n times。So if we say let us take unique color for each region。

 then that many times we have to pass the paper through a printing press to avoid this extra work。

 we want a solution so that in minimum number of colors this map can be colored so that minimum number of times it can go through and that cost of printing is reduced。

So that's how this problem is introduced， so the map can be converted into a graph and the graph can be solved so we get a solution for a。

Map， so let us see how this map can be converted to a graph。For each region。

 we mention it as a vertex。 This is a vertex， second vertex， third vertex。And so on。Now。

 the neighboring regions， we will draw an edge。 see these are neighboring， draw an edge。

 These are neighboring。 So it is a boundary common boundary which one， So this is neighboring。

Then for this second vertex， who are neighboring4 and3 are neighboring for third vertex。

 who is neighboring，4 is neighboring for fourth vertex。

 who is neighboring5 is neighboring and two already done so this is forming a graph so if I take this graph 1。

2，3，4 and 5。

![](img/a154013540988b66b2f0288710fa1a86_89.png)

Then。

![](img/a154013540988b66b2f0288710fa1a86_91.png)

This is for me， a graph。

![](img/a154013540988b66b2f0288710fa1a86_93.png)

This is forming a graph。 Now， solve this m coloring problem on the graph。

 Whatever the vertices will get color， that same color you fill them in this regions。

 So the problem is solved。 So nowadays， we are using printers。

 which will print the entire thing in one shot， it will use all colors。

 mix them and print them at once。 But in olden days for every color we have to pass it through the machine and let the paper dry then again pass it through the machine。

 So that was a lot of time consuming work。 So this was a very famous problem in olden days。

 that is coloring the map。 Now， even if any other problem。

 which you think that it is suitable for this one， then you can convert into a graph coloring problem and solve that problem。



![](img/a154013540988b66b2f0288710fa1a86_95.png)

![](img/a154013540988b66b2f0288710fa1a86_96.png)

So that's all about graph coloring。

![](img/a154013540988b66b2f0288710fa1a86_98.png)
# 【精译⚡算法导论】AbdulBari p61 p60 5.1 Graph Traversals - BFS & DFS -Breadth First Search and Depth First Searc -BV1hhPXeTEWM_p61-

Hi， the topic is breadthful search and De search in this video I'll cover these two traveral methods by taking various examples。

Breakfat search and defer search are graph traveral methods。

So we'll understand quickly the difference between them through this a small example。

 then afterward I'll take another example and I will explain you in detail。



![](img/7a209dd5421b6e8b41df275a5b01620c_1.png)

Now for quick understanding， I have taken a simple graph actually it's a tree。

 but a tree is also a graph。 So let us see So for traver cell。

 both of these traverse cell we have to know these two terms。

 Now for understanding these traverse cells we should know two terms one is visiting a vertex means going on a particular vertex Second term is exploration of vertex exploration means if I am on sub particular vertex then visiting all its adjacent vertices is called as exploration。



![](img/7a209dd5421b6e8b41df275a5b01620c_3.png)

So based on these two terms， we can understand traverals。

 So first I will explain you breakfast search Cm selecting vertex1 as the starting vertex to find out breakfast search。

 you can select any vertex as a starting vertex。

![](img/7a209dd5421b6e8b41df275a5b01620c_5.png)

![](img/7a209dd5421b6e8b41df275a5b01620c_6.png)

![](img/7a209dd5421b6e8b41df275a5b01620c_7.png)

Now， vertex 1， I will visit the vertex 1。Now， once the vertex is visited。

 this vertus I will start exploring means I will visit all adjacent vertices。

 so who are those54 and 2 in which order I can visit I can visit them in any order so okay I will take two first then4 then 5。



![](img/7a209dd5421b6e8b41df275a5b01620c_9.png)

Next。I should select the next verortex for exploration。

 so these are already visited vertices After one I have visited 2，4，5。

 then I should explore explore what I will explore two so who are resistant to2 adjacent to2 or 76。

3 in which order you can take you can take them in any order。

7 then three then 6 in any order you can take。That's all all the vertices are visited and there is no vertex remaining for exploration。

 This is breadth first search。 Now， let us look at depth first search。I'll start from vertex 1。

Then from one， I have start exploration， so I'll go to vertex 2。Do。Now。

 who are other adjacent vertices4 and 5， No， don't visit them。You have reached a new vertex。

 so you start exploring that vertex。 Okay， I'll start exploring to， then who are adjacent to this 7。

6 and 3， so I want to go to3 Okay go to3 then shall I visit6 and 7 Also no this is depth first search start exploring3。

So if I start exploring three， there is nothing connected to three。Okay。

 so it means three is completely explored， then come back and then continue the exploration of two。

 So who are there6。Explore 6。 Nothing is there。 Come back。 Go to 7。 Explo 7。 Visit 7。 Explo 7。

 There is nothing。 So come back to one now and continue the exploration of one who are adjacent to it 4。

 visit 4 and explore 4。 There is nothing。 come back。 Then go to 5，5。 Now in this way。

 all are explored。 So the tra cells are different。

![](img/7a209dd5421b6e8b41df275a5b01620c_11.png)

![](img/7a209dd5421b6e8b41df275a5b01620c_12.png)

![](img/7a209dd5421b6e8b41df275a5b01620c_13.png)

![](img/7a209dd5421b6e8b41df275a5b01620c_14.png)

Wes are different， so in breadth search， we will explore a vertex。

 then we go to the next vertex for exploration， but in depth first search。

 once we started exploring once we visited a new vertex。

 we will suspend this vertex and start its exploration。So from one， we got two。

 So we started exploring2。 then from two， we went on three。 So we'll start exploring three like this。

So an defer search approach is different and breakfast search approach is different。

 so I'll take one more example and explain you what is the difference between breakfast search and defer search with a simple example。



![](img/7a209dd5421b6e8b41df275a5b01620c_16.png)

One more example。Let us find breakfast search。Actually， this is a binary tree。😡，3 is also a graph。

 so let us perform breakfast search and C。 So as per binary3， I will perform level order， one。

 then 2，3。

![](img/7a209dd5421b6e8b41df275a5b01620c_18.png)

Then four， five， six，7。4，5，6，7。This is breakfast search means breakfast search is just like a level order on a binary tree。

Then what is the depth for search？Visit one。 Okay， Exp one。 So we got two。

 So stop exploring  one and start exploring 2。 So 4。 stop exploring 2 and continue exploration of 4。

 There is nothing。 So go back and come to 5。 Now， nothing is remaining。

 So go back to one and come on the site。

![](img/7a209dd5421b6e8b41df275a5b01620c_20.png)

Then 6， then go back and 7。 So this is like pre order。 So breakfast search is just like level order。

And。Thatpt for surge is just like。Preor drivers of a graph。I have taken a bigger graph now。😡。

We will learn about breakfast surge and def in detail。First of all。

 B search for performing breakfast search， I will take one data structure that is Q。

I have taken a cu。Now I'll explain you initial step， then I will explain you repeating step。

 so what is the initial step。

![](img/7a209dd5421b6e8b41df275a5b01620c_22.png)

Start exploration from any one of the vertex。 So which vertex I should select as a starting vertex for bit for such。

 you can select any vertex you like。

![](img/7a209dd5421b6e8b41df275a5b01620c_24.png)

So I'll select ver X 1。So in the answer， you show it one in the graph you draw here again。

 then add it to Q。This is the first step， initial step。Now， we will perform repeating steps。

 So what are those repeating steps。 Take out a vertex from Q and start exploring it。 So vertex 1。

 who are adjacent to 1，4 and 2。 So explore them。 So first I want to visit 4。 Okay。

 add it to result and also add it to Q。 Next， I want to go to 2。 Okay。

 add it to result and also add it to Q。 Now one is completely explored。

 There is no adjacent vertex remaining for vertex 1。



![](img/7a209dd5421b6e8b41df275a5b01620c_26.png)

![](img/7a209dd5421b6e8b41df275a5b01620c_27.png)

This is pho iteration completed。Nowor repeat the procedure。 What to do next。

 select next ver X for exploration from Q。 That is 4。 Start exploring 4。 So who is adjacent to 4，3。

 So I am drawing it like a3 here。 So3 is adjacent。 So add it to Q。 Any other adjacent for4。

 Nothing is adjacent for4。 So4 is completely explored。 Now， select next verex for exploration。

That is two。 who are to two。

![](img/7a209dd5421b6e8b41df275a5b01620c_29.png)

3，5，7，8。 I can visit them in any order if I check3 is already explored。

 so then I will prefer going on 5 first， So5，5。 Next， I want to go on 8， Okay，8， so8 and 8。 next。

 I will go on 7， so 7 and add 7 here。😊。

![](img/7a209dd5421b6e8b41df275a5b01620c_31.png)

![](img/7a209dd5421b6e8b41df275a5b01620c_32.png)

![](img/7a209dd5421b6e8b41df275a5b01620c_33.png)

Not two is completely explored。Now， select next verex for exploration。 Who is that 3。

 Is there any additional what this is for3， Yes，2，8，9 and 10。 So 2 is already visited。 So first。

 I will take 10。

![](img/7a209dd5421b6e8b41df275a5b01620c_35.png)

跟。Then0， and the 9。9， added to cube。

![](img/7a209dd5421b6e8b41df275a5b01620c_37.png)

Complelette it，3 is completely explored。 Now， select next verex for exploration 5。



![](img/7a209dd5421b6e8b41df275a5b01620c_39.png)

Anybody are just to5 yes 8 and 7 and 6。 So8 already visited7 already visited6。



![](img/7a209dd5421b6e8b41df275a5b01620c_41.png)

![](img/7a209dd5421b6e8b41df275a5b01620c_42.png)

This is 6。 So 6 and 6。

![](img/7a209dd5421b6e8b41df275a5b01620c_44.png)

5 is completely exploded。Select the next verortex for exploration8， who adjacent to 8。



![](img/7a209dd5421b6e8b41df275a5b01620c_46.png)

2 and 7，2。 actually， we came from there 7 Do dotted line。



![](img/7a209dd5421b6e8b41df275a5b01620c_48.png)

So vertexus is already visited， we are drawing a dotted line。The next verdictex for exploration 7。

7 is already explored。 So is there anything remaining for 7， No，10， there is nothing nearer to 10。

 No， nothing adjacent to 10。 There is nothing as adjacent to 9， and there is nothing adjacent to 6。

 So that's all this is breakfast search completed。 And the three that we got here is。

Breakfast search。Spanning dream。Dotted edges that we got here。 They are called as。Cross edges。

 They are called us cross edges。Let us see what are the things that we have learned。

 First thing is you can start breakfast search from any vertex you like。 First point。

 Second thing is when you are exploring any vertex1。

 then you can visit the suggestion vertices in any order you like。



![](img/7a209dd5421b6e8b41df275a5b01620c_50.png)

This for the second thing， then both are leniency is given。 Freedom is given to select any vertex。

 Then what is the rule here， rule is。

![](img/7a209dd5421b6e8b41df275a5b01620c_52.png)

When you are selecting a vertex for exploration， you must visit all its adjacent vertices。

Then only you should go to the next verortex for exploration， so if I am exploring one。

 then I should visit four as well as a two， then only I should select four for exploration。



![](img/7a209dd5421b6e8b41df275a5b01620c_54.png)

![](img/7a209dd5421b6e8b41df275a5b01620c_55.png)

This is the rule。The next thing is。Lasting is。You should select an next vertex for exploration from a queue only。

 So Q and exploration should be completely done。 These are the two important points about breakfast search。

 Follow this one， then you can get many answers。 I will write few more valid breakfast searches here。

First one。I'll start from vertex 1， then I'll explore the adjacent vertices so first I'll explore2 then4。



![](img/7a209dd5421b6e8b41df275a5b01620c_57.png)

Then I have to start exploring two because I have visited two first so who are adjacent to2 so I will take eight then five then7 then three these are adjacent to two all these are adjacent to2 then I should explore which one4 so who are adjacent to 4。

3 salary over then explore8 who is adjacent to85 and 7 both are visited now explore 7。So this is 6。

 Now， explore 3。 So 10 and 9。 So 10 and 9。 This is one also， this one is also a valid answer。

Then one more。 I'll start exploration from 5 from 5 who are adjacent to 8，7 and 6。Now explore two。

 who are resistant to two， three and one。No， exploit。7 is already visited，7， Everything is visited，6。

 nothing is there。 So everything is visited。 Exploore 3， So 9 and 10。And 4。 So for 3，9，10 and 4。

 I have visited。 Now， exploreer1， nothing is remaining 9，104， not all are visited。

 So this is also valid。

![](img/7a209dd5421b6e8b41df275a5b01620c_59.png)

So like this， you can start from any vertex and you can visit the adjacent in any order so you can form numerous number of valid。

Breakfast search。Next you will see depth first search。 Now next is depth first search for this。

 I will take a stack stack is a data structure used here。Let us start。

I can start the traveral from any vertex I like， so I want to start from vertex1， so one is visited。

This is the initial step。Now the repeating step， what I have to do every time。

As this new verorex is visited， start exploring it。 So are registered to that 4 and 2。So， visit for。

Fd。4。Now， the rule in depth searches。

![](img/7a209dd5421b6e8b41df275a5b01620c_61.png)

Once you have visited one vertex， still one more is remaining。 Leave that。 We will see it afterwards。

 First， you start exploring 4。

![](img/7a209dd5421b6e8b41df275a5b01620c_63.png)

So this is the rule， so once you have reached a new vertex， start exploring that new vertex。

What about that one， suspend it and keep it in the step that we can explore it later。

Now start exploring four。 so from four I can go on three。 so okay， go to three trees visit it。Now。

 what to do， Suspend 4 and start exploring 3。From 3， I can go on 10。

So 10 suspend 3 start exploring 10。 There is no adjacent vertex of 10。 So go back to 3。

 So how to know I will I have to go back。 This stack will give me their value。

 So this3 continue exploring 3。 so I can go on 9。9， and again， sussp3 and start exploring 9 from 9。

 it cannot go anywhere。Then go back to 3 and start exploring 3。 So who is addition to 3，2。

 So two is visited。Then from to who is adjacent， su to and start exploring to。

 So from to8 is adjacent， so take8。

![](img/7a209dd5421b6e8b41df275a5b01620c_65.png)

![](img/7a209dd5421b6e8b41df275a5b01620c_66.png)

Now start exploring 8， so from there I can go on 7， so suspend 8， so7 is visited。

Now we have to explore 7 from 7。 I can go on 5。So P is newly visited now we have to start exploring5。

 so suspend7 and push it into the stack。Then from five who is adjacent6， so visit6。

 suspend five and continue exploration of6。There is nothing adjacent to 6。

 So go back to 5 from 5 where I can go further so I can visit 2， which is already completed。

Right I can visit it which is already completed， so there is nothing remaining for five。

 So what happens in this way is we are going deep and deep right So in this way almost all vertices are visited only they are completely explored。

😊，So5 is completely exploded。 Go back to the previous vertex。 Who is that 7。

7 from 7 where I can go from 7， I can go on 2， which is already visited。Then go back to 8 from 8。

 nothing is remaining。 So from to where I can go， I can go to one。Right， then nothing is remaining。

 So go back to 4 from 4。 I cannot go anywhere from 3，1， I cannot visit anywhere。So that's all right。

 So here is the defer search。Traversal result。 And this is a DFS spanning tree。

 This is depth for search。

![](img/7a209dd5421b6e8b41df275a5b01620c_68.png)

Spanning tree。And these edges are called as back edges。



![](img/7a209dd5421b6e8b41df275a5b01620c_70.png)

So for this graph， we can make a tree like and perform pre orderder。

 So this is the pre orderder of disit3。 See 1，4，3，10， then 9， then 2，8，7，5，6，1，4，3，9，8，2， So9，2，8，7。

5，6。So， this is like。Preor traverson。

![](img/7a209dd5421b6e8b41df275a5b01620c_72.png)

Now， I will write few more valid depth for search directly looking into the graph。



![](img/7a209dd5421b6e8b41df275a5b01620c_74.png)

I'll start from vertex 1。

![](img/7a209dd5421b6e8b41df275a5b01620c_76.png)

1， this is the first one。 from when I'll go to2。

![](img/7a209dd5421b6e8b41df275a5b01620c_78.png)

From2， I'll go to 8。From 8， I will go to 7。From 7， I'll go to 5 then 6。 from 6， I cannot go anywhere。

 Come back to 5。2 is already completed。7 also completed。 So what was the route I have taken。

 So come back to 7。7 is completely explored。 Come back to 8。 Nothing remaining。 Come back to 2。

 So from 2， I'll go  to。

![](img/7a209dd5421b6e8b41df275a5b01620c_80.png)

![](img/7a209dd5421b6e8b41df275a5b01620c_81.png)

3， then 9， nothing is there。 Come back and go to 10， then go back to 3 and go to 4。

Then one is already explored， so return back to four then three then2 then one finished。So。

 this is one answer。Then one more rally show。I'll start from vertex 3。Fast is 3。

 Then I'll visit to 4， then  one， then 2， then 5， then 6 from 6 and 8 cannot go anywhere。

 Come back to 5。 Come back to 5 and go to 7， then 8。Right from8 I am back on two but is already over。

 so complete go back to7 then five then come back to2 then two from there I have already gone to。1。

1 is already completed， right， So come back to4， then come back to 3。 So from3。

 who are remaining10 and 9。 So 10 then 9。This is also valid。

So you can start from any vertex you like and you can visit any neighbouring vertex。

 but only thing is once you have visited a new vertex。

 suspend the exploration of current vertex and start exploring new vertex。

Thats all about defer search and breakfast search。 And the time complexity of both these methods is orderov and。



![](img/7a209dd5421b6e8b41df275a5b01620c_83.png)

And this number of whattices。
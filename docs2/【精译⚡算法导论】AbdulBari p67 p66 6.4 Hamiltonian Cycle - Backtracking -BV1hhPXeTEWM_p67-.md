# 【精译⚡算法导论】AbdulBari p67 p66 6.4 Hamiltonian Cycle - Backtracking -BV1hhPXeTEWM_p67-

Hi， the topic is Hamiltonian cycle in this video we will learn what is Hamiltonian cycle。

 then I'll show you how to solve it using backtracking using an algorithm I will explain you how backtracking is useful for solving the problem。



![](img/e896f0b17d7f4f0efeef271e940d644c_1.png)

![](img/e896f0b17d7f4f0efeef271e940d644c_2.png)

First of all， let us understand what is Hamilton in Cy。See if a graph is given。

 then we have to start from some starting vertex and visit all the vertices exactly once and return back to the starting vertex。

So that forms a cycle， so we have to check that is there any Hamilton in cycle possible in a graph if possible then what is a cycle and if there are multiple cycles we have to find out all those cycles。

So the problem is to find out if there is any Hamilton cycle in a graph or not。

So the problem looks similar to traveling salesperson problem in traveling salesperson problem。 Also。

 we have to start from some vertex， visit all the vertices and return back to the starting vertex。

 But that is a minimization problem where we have to find out a minimum cost tour。 But here。

 if you take it as a tour。 we have to find out all possible tours。 Now。

 let us know few important things。 First of all， the graph given may be directed or non directeded。

But it must be connected if it is not connected， then the cycle is not possible。

 means if a graph is having multiple pieces， multiple components。

 then it is not possible to have a Hamilton in cycle in a graph。And one more thing is。

 this is a N hard problem。Means exponential time taking problem。

 So there is no easy way to find if there is any Hamiltonon cycle present in the graph or not。



![](img/e896f0b17d7f4f0efeef271e940d644c_4.png)

So let us manually find out if there is any Hamilton cycle in a graph， let us take this graph first。

I'll start from vertex 1， then I will visit vertex 2， then 3， then 4， then5， then 6， then1。



![](img/e896f0b17d7f4f0efeef271e940d644c_6.png)

Then 1 to 2，3， then 4， then 5， then 6。 and one。 this is one second。



![](img/e896f0b17d7f4f0efeef271e940d644c_8.png)

Even I can go from 1 to 2，2 to 6， then 6 to 5，5 to 4，4 to 3， then 3 to1。

 So I have one more cycle 1 to 2，2，2 6，6 to 5，5 to 4， then 3， then 1。



![](img/e896f0b17d7f4f0efeef271e940d644c_10.png)

![](img/e896f0b17d7f4f0efeef271e940d644c_11.png)

One more cycle， one to six， six to two then two to five， then five to four，4 to three， then 32， one。

 so one two six， six to2，225， five2 four， four to three， then three2 one。



![](img/e896f0b17d7f4f0efeef271e940d644c_13.png)

![](img/e896f0b17d7f4f0efeef271e940d644c_14.png)

![](img/e896f0b17d7f4f0efeef271e940d644c_15.png)

C， you can find that there are more than one cycles possible。

 So the problem is we want to find out all possible Hamiltonian cycles in a graph。



![](img/e896f0b17d7f4f0efeef271e940d644c_17.png)

If they are possible or not， if they are possible， then how many are possible， we want all of them。

なで one moreサラで show you。嘟嘟。3，3，2，4，4，2 5，5，2，6， then 6，2，1。



![](img/e896f0b17d7f4f0efeef271e940d644c_19.png)

2，2，3，3，2。4，4，2，5，5，2，6，6，2，1， and then 1，2，2。

![](img/e896f0b17d7f4f0efeef271e940d644c_21.png)

1 to two， one more cycle。No， wrong。 See。 this is same as the second。

Same as the cycle that was starting from one and is starting from 2。

 So if you change the starting point， the cycle has not changed。 You see the order of whatex says 2。

3，4，5，6，1， then 2。 So 2，3，4，5，6，1 then and two。 So we are getting in the same order。

 So this is not another cycle is's the same cycle。 just you are taking the starting point as some other vertex。

 So you have to also take care that you are not taking the duplicate cycles or you are not taking the same cycle again。



![](img/e896f0b17d7f4f0efeef271e940d644c_23.png)

![](img/e896f0b17d7f4f0efeef271e940d644c_24.png)

![](img/e896f0b17d7f4f0efeef271e940d644c_25.png)

That's it。 Now， I have few more examples here from this Also we observe few things。

 and we will learn few facts about Hamilton and cycle。



![](img/e896f0b17d7f4f0efeef271e940d644c_27.png)

There is a graph given。 Let us find out if there is any Hamilton in cycle in this  one，1 to 2。

 then 2 to 3，3 to 5， then 5 to 4， then 4 to 1。 This is one cycle。 One more cycle。

 Let us check one to 2 then 2 to 4 then。4our to5 then5 to3 then three to1。

 so there are more than one cycle is possible。 let us try in this graph 1 to2 then  two to 3 then  three to 7 then 7 to 6。

 then I have to go on four if I go on4 I cannot come to5 If I go on five I cannot go on four。

 so Hamilton cycle is not existing in this graph。

![](img/e896f0b17d7f4f0efeef271e940d644c_29.png)

Let us take this graph 1 to2 then 3 then 4 then  three， then I will go to6 and then 5。

 I cannot come back on one again。 I have to come via three。

 So on such graphs hammer and a cycles are not possible。

 why because this vertex is a junction for a graph or a connecting point photograph and this is called as articulation point。

 So if there is an articulation point in a graph， then have and cycle is not existing in a graph。



![](img/e896f0b17d7f4f0efeef271e940d644c_31.png)

![](img/e896f0b17d7f4f0efeef271e940d644c_32.png)

![](img/e896f0b17d7f4f0efeef271e940d644c_33.png)

![](img/e896f0b17d7f4f0efeef271e940d644c_34.png)

![](img/e896f0b17d7f4f0efeef271e940d644c_35.png)

Let us look at this one，1， then 2， then 4。 Then if I go on5， we cannot come back and go to3。

 So here also it's not possible because these type of vertices are there。

 They are called as pendant vertices because of this pendant vertices。

 Hamilton cycle is not existing in a graph。 So we learn two more things that if an articulation point。

 then Hamiltonton cycle， not possible in a graph。

![](img/e896f0b17d7f4f0efeef271e940d644c_37.png)

If there's a pendant vertex， then also Hamilton cycle is not possible in a graph。 That's all。

 I have explained you about Hamilton in cycle。 Now， I will take a algorithm and an example graph。

 Then I will show you how back trackinging helps us in solving this problem。

 Let us look at the algorithm and understand how back trackinging is useful for solving this one。

 I have a graph here。

![](img/e896f0b17d7f4f0efeef271e940d644c_39.png)

![](img/e896f0b17d7f4f0efeef271e940d644c_40.png)

And this is the adi matrix for graph。This is the algorithm。

 which is having two methods or two functions。So two pieces of code out there。

This is the starting point and this is using this algorithm。😡。

This is performing backtracking and for getting the next verortex， this is helping。

I will not trace it right now。 first， I will show you the working， explain you the working。

 Then from the working， I will just point out which line was doing the work that I have shown you。



![](img/e896f0b17d7f4f0efeef271e940d644c_42.png)

So let us start。This algorithm uses this a matrix， and it uses this array for finding the cycle。

 so whenever all these values are filled and the cycle is found， it will display the result。Now。

 initially all these values are zero， let us start。Now， let me start。

 I'll explain you through state space 3 to understand the working of an algorithm。

 And if you remember backpacktaing works just like depth first search。

 it performed depther search on the problem。Let us start。We don't want a duplicate cycle。

 so we will fix the starting vertex。 So we make the first vertex that is starting vertex is1。Now。

 here we may be getting different vertices。 So this is the starting vertex 1。

 So let us start a state spacee tree。 Now， we'll start from the second position on words。

 What should be the second vertex。 If you are starting from one， then where should go。

 you should go on3 or two or 5。 What all the possible we will try here。

 So this Hamiltonian algorithm will start from this vertex。 So what it does I'll explain here。

 I will not show their line by line， I'll explain here。 See it will try to put one here。1。

 this is same thing only。 This is already there。 So if there is any vertex that is appearing again。

 it will avoid that。 Then it will try to here。 Yes，2 is not already is not present。

 The next thing is there any edge from 1 to 2。 So here，1 to 2，1 to 2。 Yes， there is an edge。

 So this is valid。 So take this one，1 to 2。Then it will go on to the next position。

 So here it is already 0。 So for C make it as one。 and check if it is already there。 Yes。

 it's solid there。 So keep here 2。 It's solid there。 So change this to next value 3， It's not there。

 But there should be an edge between 2 and 3。 So 2 to 3， there is an edge。 Yes， there is an edge。

 So it's valid。 So 2 to 3， there is an edge。 So from one， we went on 2。 the next step is what3。😊。

Then it will move on to this one。 See， once the vertex for this position is finalized。

 it will move to the next one。Then here， it will try to keep one。Already appearing2。

 already appearing。 See these values I'm not showing here。 I can even show like， this one。

1 bonding function。 If you remember the bounding function is used in back trackinging that will kill the node。

 See if I write one here is invalid，2 also invalid，3 also invalid， then 4。

 So I'm not writing all invalid nodes。 So here we try one， then two， then。3 is already there。 So 4。

Check， is there any the edge from 3 to 4。 Yes， it's there。 so include four。The next here。

 one invalid 2， No， not possible 3，4，5。 Shall we have 5 here， and check 4 to 5， is there edge。 Yes。

4 to 5， there is an edge。 So includelude 5 Also。 Now。

 once you have reached this position in an array， fifth position in an array also verify that from 5 to 1。

 there is an edge or not 5 to 1。 Yes， there is an edge。 So it means a cycle is found。

 print this result。This is the first answer we got。First answer we got。Priend this reservation。See。

 here， I will show you。See， it was calling for the next vertex and。X of k plus 1 more than plus 1。

 What is that， I explained。 So K plus  one。 So it was checking next value After taking the next value is for checking whether it's becoming 0。

 No， then is there any edge， Yes， edge is there。 Check。 It should not be duplicate。

 This code is for checking duplicate。 See， I was telling that when I take here to suppose to is already there。

 Don't take it。 Then try next value X plus1。3 is already there。 Don't take it。

 So there is an edge in between them also， and there should not be any duplicate。

 And if you have reached the last position that is fifth position in an array， fifth position。

 then also check that there is an edge back to verex 1 that it should not be 0。 It should be 1。

Thats it。 So this is how it is verifying this is the part of a bonding function taking the next work vertex and checking whether it is already taken is it duplicate。

 I there an edge from previous vertex。Is it having a edge to the first vertex。

Let me explain you what other things that are checked in bounding function。 First thing。

 you should not take duplicate。 Second thing， whenever you take any vertex。

 there should be an edge from the previous vertex。 Second thing， Third thing。

 if you are on the last vertex， then there should be an edge to the first vertex。 If so。

 then is an answer。These are the things we check in the bonding function。

 so this is what it is trying with the bonding function。So we have finished till here。

 Let us continue the algorithm 5 tried the mixed value， it will become 0，0 means stop， right。

 So stop pins go back where this one。Here at this place， see， this is the starting point，1，2，3，4，5，1。

2，3，4，5。 Instead of 4， what is the next value that can be taken 5。

Check is it already appearing No so5 is not there so it's valid 3 to 5 there should be an edge 3 to 5。

3 to 5 is there is no edge。 no we cannot take this so take the next value So after 5 comes what 0 So it is just like this0。

1，2，3，4，5 then 0 again then1，2，34 then 0 again so that is the method so mod gets the values like that。

Alright， more than plus 1，5 plus 1，6， if you do， you get the values like this。

So we cannot try anything here。 Then go back。 It will go back to this one。 third here。 See 1，2 over。

1，2 over for the third1 instead of writing 3。 Can we write 4 here。 Next value。 So 2 to 4。

 there should be an edge。 So here I will show you2 to  four years， there is an edge。 So after 2。

 take 4。 then to the next one， write，1， not valid 2， not valid。3。Valed， but 4 to 3。

 there should be an edge。 Yes 4 to 3。 There is an edge。 So take 3 also。The next one。

Can I write one here。 No， already there 2 Also， already there。

3 Also already there 4 Also already there 5。 I can write this one， But a 32 5 is there in edge。

3 to 5。 No， this is not valid。 So take it as 0， right next value， 0。

0 means come back and write 4 here， not valid。5 here。 Yes， it is valid。 So this was bounded。

 This was killed。 So at this place。 instead of 3。 Now， we can write 5。 So 4 to 5， there is an edge。

 Yes， there is an edge。 So we can write 5 here。😊，Now next place I cannot write one，2。

 but I can write three here。 If I write three here。5 to3， there should be an edge。

 No5 to 3 there is no edge So here we cannot write 4 or 5 so write0 and here also 0 come back next value of 4。

5 So at this place after2 it is 5 next here what it can be kept here，1，2。

3 can be kept then 5 to3 we know well that there is no edge so next four can it be kept yeah4 to 5 it's there So 4 then next here three can be possible so4 to 3 there is an edge。

 yes， then3 to1 is there in edge。 yes，3 to 1 there is an edge so what is the path we got1 to 2。

2 to 5，5 to4，4 to3，321 So so far we got two answers。 that is1，2，3，4，5 and1 now here also1，2，5，4。

3 and then one So we got two answers。

![](img/e896f0b17d7f4f0efeef271e940d644c_44.png)

If you continue， you may provide all possible Hamiltonian cycles in this one。

So I have taken an example and explain you。Right， now I will show you the algorithm。

I'll explain the algorithm。 So you will start from vertex 2 in vertex 1 first place。

 we will write one only fixed from second place onwards， we will try。 So what it will do。

 it will try to find out the next value。 So what is the next possible value， What are the condition。

 the value that you have taken should not already existing means here you cannot take 12。

5 and 4 here， you cannot take those things。 First condition。 Second thing。

 whatever you have taken here， then there should be an edge to the previous one。

This should be an edge to the previous one。 K， whatever you have taken K-1， This should be an edge。

 It should not be0。 in this graph。 It should not be0。 This should be an edge。

 And this follow is for checking duplicate。 It should not already be existing， two things。

 And the last thing is， if this is the last place。 then this should have an edge to verex1。

 So if this is the last place， then there should be an edge to the first one。

 This are three things check in the condition。 So this will try all possible values for a place。

 So what are the values it started from 0， actually， right，0。

 then one then two then three then  four then 5。 All these values it will try here。

 Similarlyly here Also， it will try and here Also， it will try here。 for every position， It will try。

 And it will try recursively， So it looks like depth first search like this。

 So this is the code for actual Hamiltonia。 It will check the next value。 If the value is not0。

 and it is last place， then it will print the answer。

Last place print the answer and will not go further， and it will go back。 If it is not the last node。

 then it will call recursively Hamiltonian for next word escape plus one means once we got the answer。

 which is not 0， we'll go for the next。 If the answer is not 0， we go for the next。

 If answer is not 0， and we have the last， we print will not go next， but it will go back。That it。

 this is how Hamiltonian cycle algorithm works。 Now， most of you are preparing for the examination。

 So for the examination purpose， you have to explain what is Hamiltonilian cycle just in one or two sentences you can finish it。

 and you have to define the bonding function。 These points you define clearly。 That is better。

In words only， you don't have to write on the code if they ask for code。

 you can write it or you can write your own pseudocode。

 You don't have to write the loop and all just write it in words for mostly for university examinations I am talking about。

 So algorithm is important in Hamilton and cycle mostly right tracing tree is not useful here because tracing tree it can expand to a very bigotry also if you try all possibilities。

If the number of vertices are growing， then the height also grows and the number of nodes also grows。

So if at all， for explanation， if you want， you can write on this one。 And the last thing， see。

 I'll remove this here，5 places，1，2，3，4，5 places。 This was fixed out of 4 places。 What we tried，2，3。

4，5，2，3，5，4，2，3，2，5，4，5，3， all possibilities。 So this is nothing but what，4 factorial，4 factorial。

 the algorithm is trying 4 factorial possibilities，4 factorial。

 So for al veres graph and -1 factorial。😊，RightN -1 factorial。 it is roughly n factorial only。

 and n factorial is big of N power N。 if you know this。

 So the time complexity of this algorithm is N power N。 that's all about this problem。


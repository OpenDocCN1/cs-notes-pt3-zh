# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P19：19_04_07_单元-2-6-视角与展望.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/3e11aed7c5bb5ea00fc7004096ccaa7e_0.png)

Welcome to the perspective unit of the second week in Nantotetriris during this week we built an AU and in the next week we're going to put this AU on the side and focus on building some memory systems leading up to a RA unit。

 but this is something that we'll do next week， let us now look back and bring up some questions that typically come up when we talk about combinational logic and AU design。

The first question is we've already built about 20 chips in this course， are these chips standard。

 namely are they typically being used in many other computer system or are they specialized to the computer that we build in this particular course？

No， most of the gates that we build in the course are completely standard， the Ha adders。

 the full adders， the adder， these are completely standard。

 as are the gates we built last week like the multiplex or Xor gates and so on。

What is not a completely standard is our AL U， which is extremely simple。 In this course。

 we clearly emphasize simplicity over almost anything else because we want to fit everything into one course。

So for that reason， our ALlu is extremely simplified in its implementation， and in this respect。

 it's a bit unique among usual As。 The next question is directly related to the previous one and the question is how come the AU that we built does not feature more operations like multiplication and division。

Well， the answer is that indeed theres no problem to write a HDL code that specifies chips that carry out multiplication and division by operating directly on zeros and ones on bits。

 and in fact， there are some very elegant and very nice algorithms to do just that。But in general。

 when you build a computer system， the overall functionality that the system provides is divided between the hardware and the operating system that runs on top of it。

 so it is the designer's freedom to decide how much functionality to put in each one of these layers when we designed the hec computer。

 which is the computer that will continue to build in the course， we decided。

 as Noam explained before， that the earlier will be extremely simple。

 and that operations like division and multiplication will be delegated to the software that runs on top of this computer。

And indeed in the second part of this course in NanttotetririsPA2。

 we are going to design among other things， an operating system。

 and the operating system will have several libraries and one of these libraries is going to be called math and the math library will feature all sorts of very useful mathematical operations。

 including multiplication and division。So at the end of the day。

 the programmer who writes programs that have to run on this computer will not feel the difference。

 The programmer will not really care if a certain algebraic operation is being done by the operating system or by the hardware it will be completely transparent for the highlevel programmer。

 but of course theres there's some tradeoff here， and typically when you design an operation in hardware。

 typically it runs much faster， but it's costly to design and it also costs money to manufacture the the more complex hardware unit。

 So once again， it's a matter of tradeoff cost effectiveness and that's how we decided to build the hec computer。

 simple Alu and many extensions later when we build the operating system。

 We hope that we convince you that the AU that we design and this course is indeed simple。

 and now the next question is。Is this value actually efficient？

Almost everything that we did in the construction is completely efficient。

 that you really can't save much more。 but there is one one component which where some important optimization is still possible。

 And it's probably worthwhile to talk for one second about the kind of optimization that we're talking about。

 And this is the adder。 So let us see what is the main problem with the adder and how one may may decide to improve upon it。

So let us recall the implementation of the adder。The address was constructed with a sequence of full addresss inside it。

Each full ladder got some inputs。From the input of the adder gate。

 And then the important thing that one of its outputs， the carry went on to the next adder。

 The next full ladderer。 Similarlyly， the output the carry from this full adder went down to this full adder and so on。

So this chain of connections is really the problematic one that one way to wish to optimize。

So let us look at the distance， if you wish， how many gates must the signal signal traverse between the input and the final output of the last full letter。

 It needs to go inside the first full ladder， go through a few gates， then go here。

 go through another few gates。 again， another few gates and so on。

 So assumes that there are like three or four gates in each full ladder。 If this is say a 32 bit。😊。

A full 32 B adder。 Al， we have 32 bits times 3 or four gates of delay。From input to output。

 And when you actually run the such hardware in a system。

 you will have to take this delay into account because it actually takes time for the signal to traverse for all the capacitor capacitors in the implementation of all these full address to actually completely load and so on。

 So having such a long chain is not considered a good thing， because it actually increases a delay。

 So what could you do instead。😊，Really， if you want to shorten the chain。

 then maybe you can compute this。To think the carry that goes into one of the full addressers at the top。

 It's it's the most significant bits compute it in a different way， not through all this long chain。

 And in fact， if you actually look at the logic that's computed here， there are more efficient ways。

 a ways that has have less delay。 And what you could do is do what's called carry look ahead。😊。

Compute this carry independently of this long chain。 So that may duplicate if you wish some effort。

 but at least you're minimizing delay。 So instead of just having the carry be computed by this long chain。

 have the carry be computed separately for each one of the full address in that least delay way possible。

 And that is called carry look ahead and that will allow you to run this chip at a much faster rate。

 because the delays are shorter。 All right， moving along。

 the last question that we want to focus on is。😊，Why do you recommend using built in chips in Project  two instead of the chips that we actually built in Project 1？

Well， first of all， you're welcome to use the chips that you built。

 you know we definitely don't prevent it and it makes a lot of sense to use the chips that you actually built because this is what this course is all about。

 we are building a complex machine which consists of various layers of construction and it is perfectly reasonable that when you build a certain layer you will use layers that you built before。

 however there are very good reasons why you should want to use built in chips that we supply rather than the chips that you built yourself。

And the most important of these reasons is the notion of we can call it local failures。

 and the idea is that if you build， I'm sorry， if you use built in chips as your chip partss and some problem raises its ugly head in the present project。

 then you are guaranteed that this problem can be attributed to bugs and problems that were created in this project only and not in previous projects。

So this is also sometimes called the notion of unit testing。

 you test each unit separately from the rest of the system。

 and this principle of unit testing goes hand in hand with other very important principles like obstruction and modularity and taken together。

 you know one of these things that these principles imply is that once you finished building a certain module you can put it away。

 you can stop worrying about its implementation and use only the interface or the API of this module when you build more complex functionality。

This really is the only way to manage complex projects。 and by adhering to these principles。

 which we find extremely important by doing so， we can really take this super ambitious project of building a modern computer from first principles and do it only in seven weeks。

 Shiman。Yes， I think we should also confess that our simulator is not that efficient。

 especially when we get to more complex projects。 if you actually run the layer。

 the chips that were constructed in previous project。

 our simulator will have to face a huge number of arrays and will simply be slow。

 if you do it using just the definitions of the previous chips。

 just the specifications of the previous chips， then our simulator will be fast and nice to work with Yes。

 in fact， that's another very important technical reason why we want to use builtin chips。

 and this problem will come up later in the course when we build memory systems and more complex functionality。

 And indeed， this is a very good other reason why it makes a lot of sense to use software based built in chips。


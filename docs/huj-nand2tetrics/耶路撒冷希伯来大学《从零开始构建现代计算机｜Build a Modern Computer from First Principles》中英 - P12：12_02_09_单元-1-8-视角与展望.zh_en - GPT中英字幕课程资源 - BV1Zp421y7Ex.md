# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P12：12_02_09_单元-1-8-视角与展望.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/cb609e3b92967d7a8a0c3aaea79713ea_0.png)

During the first week of this course， we built a suite of 15 elementary logic gates。

And in the next week of the course， we're going to take this basic functionality and use it in order to build some more interesting and powerful chips like Eders and arithmetic logic unit。

Now whenever we teach this course， every week of instruction there's a whole set of issues and questions that come up about different aspects of building hardware and software systems。

 so we've decided to devote the last unit of each week to answer such questions and we are calling this unit this last unit every week a perspective unit。

 so here are the questions that typically come up at the end of this unit in which we deal with elementary logicgates。

So the first question of the day is。Is it possible to build a computer starting with a logic gate other than N。

Well， I'll take this question。And the answer is， indeed， yes， it's possible。 For example。

 you can use another elementary gate called nor， which stands for not or and base your entire computer on this atomic building block。

 Likewise， it is quite natural to start with a suite consisting of end or and not gates and use them to build the system。

 And there are a number of other possibilities。And in fact。

 it's quite similar to the way geometry can be founded on different sets of axioms。

 and each one of them can be yet another point of departure to build， you know。

 all the power and theorems of geometry。 This is not such a bad analogy。However。

 it turns out that N gates are very popular in physical implementations of hardware systems because there are many integrated circuit technologies in which it is quite cheap or relatively cheap to build N gates as you well know during the course during the first week we treated these N gates as black box abstractions so the next question which is directly related to the first one is well。

 if you actually had to build a end gate， how would you go about it。No。

 maybe you can answer this question。 Okay， so in this course。

 we sort of made a point of not going into this question because we feel this is already physics or electronics rather than computer science。

 But still， let us see an example。 There are， of course。

 many different technologies to implement aggregate gate And any other gate。

 But let me show you let me show with the simplest example， if you wish， of such an implementation。

 So here's an Mmos。Implementation。A fer gate。We have a plus。EVtage， which is going to be one。

 our logical  one and a minus voltage， which is our logical 0。

 And we're going to connect them as follows。A little resistor here， which is the weak connection。

And then two nice transistors， and most transistors。Which we connect this way。

 This is going to be our a input， and this is going to be our B input。

 And this is going to be our output。So these are the two transistors that we have。

So how does this say implementation work， The basic functionality of one of these Nmosts transistors is that whenever the input gate has gets high voltage。

 then it connects the two other terminals。 If it gets a negative voltage inside。

 it disconnects the two terminals。 So let's see what happens。 If both A and B are one。

Then we get a high voltage here。 high voltage here。

 These two terminals are connected by this transistor。

 These two terminals are connected by this transistor。

 So we get a connection all the way from the output to negative。😊，And since this is a we connection。

 and this is a strong connection， our output is going to be negative or 0。As we want in an end gate。

 because when an end gets  one and one has inputs， it gets 0 is output。In any other case。

 one of these two inputs is going to be negative， which means a low voltage。

 The transistor connected to the low voltage input is going to disconnect the two terminals。

 in which case there is not going to be a connection from the minus sign to the output。

 And so this we connection to the plus is the one that's going to rule。

 And we're going to get a plus output， which is exactly what we want in an end gate， which is true。😊。

So this is not inmost implementation of a N gate。 There are many other technologies。

 This one is not used so much anymore since the 70s or 80s。

 And the important thing in this course is we do not care about the technologies we do not care neither about this implementation or any other implementation。

 we want to abstract at to wait a way inside of gates that get true and false and output through and false and we don't care how exactly。

So welcome back from the world of resistors and transistors， and once again。

 this is a level of detail that we are not going to get into in this course。

So here's the next question that we have。And it's about how description languages。

And the question is how does the HDL that we used in this course and in this week。

 how does it compare to real HDL languages that harder engineers normally use？Well， first of all。

 R HDL is a very real language because you can use it to design computers and simulate computers and that's what HDLs are all about。

 At the same time， obviously industrial strength， HDL languages like very log and VHDL are far more complex and powerful than our HDL。

Typically they have a syntax which is some mix of the HDL that we use and something that looks like the C programming language and they feature all sorts of high level programming constructs like for and while which eliminate the need to write a lot of repetitive HDL code so it's very nice to use these capabilities and they also feature like our language does。

 they feature the ability to model and simulate the notion of time and clocks with which you wouldn't be able to build sequential logic in our logic that ends up with with which you end up building things like memories and encounters and so on so these languages are very nice and the same time they are quite complicated and it would take you at least a month or so to master these languages in order to begin writing some code for this course。

So as an alternative， Noram and I decided decided to design a very simple dialect or a very simple version of HDL and offer it to you。

 it has all the capabilities that we need in order to build the computer that we build in this course and you can learn it in one hour The next question which is for Noam is as follows The chips that we built so far were quite simple。

How does one go about designing complex chips containinging hundreds of parts and connections？ Well。

 the truth is that there is no simple general way of designing complex circuits。

 It's really a complicated design challenge， and you need human ingenuity to do it well。

Now there are many techniques that you learn in digital circuit construction courses， for example。

 there are techniques called Carm that allow you to optimize gates with a small number of inputs Sometimes you can use various tools。

 for example， there are so-called silicon compilers where you specify what's the functionalities that you want and the silicon compiler already has inside it a lot of logic and a lot of algorithms that can optimize gates for you。

 but again， it is not perfect algorithms， these are all heuristics because the general problems is so-called NP complete。

 you cannot find a computer program that does it perfectly。😊。

The real answer is after all these tools and all these techniques and so on。

 at the end of the day you use the usual tools of computer science， modularity and abstraction。

 you break a complex problem into simpler parts and the simpler parts are simpler to optimize and to construct and at the end of the day after you use all your tools after you use all your techniques。

 you go back and use this modularity at the idea。😊。

So these were the questions that we chose to focus on in this first perspective unit of week1 as you can see this particular format of the perspective unit is openended。

 there are numerous questions that can come up。 once again。

 we don't want to deal with the level of transistors and resistors you know this is something that belongs to electrical engineering。

 we want to focus on computer science and when it comes to hardware technologies and so on。

 there are many questions that No and I cannot answer either so are we welcome any questions that can come up。

 you can post these questions on the course Q&A forum and if there are other students who are we have some knowledge about these areas you are perfectly welcome to go to the Q&A forum of the website of this course and answer these questions on your own。


# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P10：10_02_07_单元-1-6-多比特总线.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/2eddff5997f60a5d3d40c494167c54c1_0.png)

And this unit， we'll deal with a question how to deal with a bunch of bits together。Really。

 this shouldn't really be a whole unit because it's almost trivial， but still。

 because there is a little bit of technical details attached to it。

 it's probably worthwhile to spend 5 or6 minutes on this thing in a short unit。

So the basic thing we want to point out is a following thing when we design hardware， a lot of time。

 we need to manipulate a bunch of bits together。First of all， it's going to be convenient。

 conceptually convenient to think about a bunch of bits that are manipulated together as one entity and allow ourselves to think about it in a slightly higher abstraction level。

 not of the single bits， but of a bunch of bits together as one entity。

The second thing is that of course since we're going to describe our chips our hardware in hardware description language。

 of course we will need some kind of support for that in the hardware description language。

 so a bunch of bits together that are manipulated together and have one meaning are sometimes called buses coming from some Latin word meaning many or multiple something like that。

😊，So here's an example of how we can of how we can think about that。

 So when we want to add two numbers and we will build in the next week。

 we will build some kind of chips that adds to binary numbers。

 Each one of these binary numbers will have a bunch of bits， actually 16 bits in our implementation。

 but we want to think about them as numbers。So our chip that adds two numbers will be described as having two inputs and a input which is 16 bits and the B input which is 16 bits and one output which is out which also has 16 bits so in reality our chip has 32 wires feeding into it and 16 wires going out of it。

 but still it's convenient to think about it as two numbers feeding in and one number feeding out。

In this way， we can actually also think about these kind of numbers when we want to use them。😊。

So this is how the same chip will be described in HDL I'm only giving the interface here the API and omitting all the internal structure。

 which is exactly what you learn next week。So we have simply defined our inputs as A and B。

 and we have in square brackets a number 16， which means that each one of these is 16 bits。

 very much like the syntax for arrays in programming languages。Now。

 once we have this kind of notation， we can think about these numbers and entities and manipulate them in higher level chips。

 so suppose we need to build chips that now adds three numbers， each one of them 16 bits。Logically。

 we， of course， know how we can do that。 We can just add two of them and then add the third one to the sun。

So how do we do that， So we get we get is our interface， three inputs， first， second and third。

 each one of them 16 Bs， and we have need to have an output， which is just out also 16 bits。

 and we want to manipulate it to this level of abstraction。

 not looking at all the separate bits themselves。 This is how we do that in HDL。

 We have two in internal chips。 One of them adds to 16 Bs adds 16 chips that we've just seen。

 and we add the first and the second inputs and plug the result into a temporary variable called temp。

 which is also 16 bits。😊，And then we take this temporary variable and add it to the or temporary wire。

 if you wish， or temporary bus 16 wires， and add it to the third getting our final output。

 and this is how we can just manipulate inside HDL the buses as entities。Now， of course。

 we should also be able to actually manipulate and get access to separate bits in a bus because at the end of the day。

 a bus is just a bunch of bits together。😊，So here's an example of suppose we want to have a chip that gets us an input。

 a bus of four bits in this case， and outputs a single bit。

 which is the end of all the bits in the bus。How do we do that to do that。

 we will need to access bit after bit。 And then simply add them one after another。

 And this is how we do that。 And notice a syntax。 And that's the important thing， The syntax here。

 when we put an index A the name of a pin of a bus。

 We just means the specific bit that we're talking about。

 We're using the convention in RHDL that is common to most programming languages nowadays。

 that a4 bit bus has bits number 1，0，1 to and 3。 So the indices go from 0 to the bus widths， -1。

And this is how we do that。 You're gonna in the next project in this project。

 you're going have a bunch of chips that actually， that's what they do。

 So take a bunch of bits in the bus and just converge them and just mash them together into a single value。

 And we call this multiway chips。 So this we call this kind of chip here。

 And for way takes four bits and and them together。 Here's another example。

 showing how we can manipulate bits inside buses。 And in the context of another thing well do commonly in in this week's project。

 basically， taking a bunch of operations and doing them in parallel to each one of the bits in a bunch of buses。

 So in this example， we have two input buses。 and we simply want to do a bitwise and of them。

 Take the first bit of A and B and together。 and that book should produce the first bit of out。

 Similarlyly， doing set for the second bit and so on。😊，So here's how we do that。 We simply have。

 We need to have four end gates。Each one of that end gates performs the operation and one of the corresponding pairs of bits。

And we access the bits one after another， simply listing the zeros bit， first bit。

 second bit and putting the end gate on these inputs and producing the correct output immediately notice that the four bits of the output we just produced go out as as a single bus because that's how it was defined in the API。

😊，So there are a bunch of technical bunch of technical conveniences sometimes that you want to use when dealing with buses。

 For example， you may sometimes want to break a bus into sub buses。

 So the first example here shows what happens if we want to compose a bus。

 a 16 B bus from 2 8 bit buses。So so this example shows that we have in our input to8 bit by 8 bit buses called LB。

 these significant byte and MSB most significant byte。

 And if we want to plug them together into an n 16 gate。

 We can just take the first 8 bits of the bus and plug the LSB into it and the second8 bit bits and plug the MSB into it and notice notice the syntax for doing that。

 if we specify a subrange inside the square brackets in exactly this format with a dot dot notation。

 then we just get the bus being plugged into the correct subbus that we want to do it。

 we can do that on the input and we can do that on the output and we can break them in different ways。

😊，Now， different hardware description languages deal with all these issues and have different syntactic conventions。

 and of course， for our hardware description language which you will need to work with in the project。

 you can find the exact specification on the website。😊。

I would like to say just a few words about some peculiarities。

 if you wish on RHDL that you may find convenient to use。 First of all。

 allow we do allow overlaps of sub buses so you can take。

 let's say bits 0 to5 and output them as one bus of six bits and then again take bits。

 let's say three to7 and output them if another bus so simply outputting the same bus in multiple ways that may be overlapping sub buses we allow that。

other conventions that we have as internal buses are just their widths is's completely deduced。

 but what by what you plugged into them。 So you don't need to specify the widths of an internal bus internal pin。

 It's just if it was connected to a bus， it just gets the correct widthids that it was connected to。

And the third day synthetic convention that I would like to mention is the fact that if you want to plug lots of zeros or lots of ones into a bus。

 you can do it together in one command by using true or false as constants。

 and all of both of these cases， you get are multiplied。 So if you plug through into some bus。

 each one of the bits gets a value 1 and similarly for false where each one of the bits gets 0。

So now we finished this very simple。This very simple unit about handling a lots of bits together。

 and now we're ready to actually completely specify the project of this week。😊。



![](img/2eddff5997f60a5d3d40c494167c54c1_2.png)
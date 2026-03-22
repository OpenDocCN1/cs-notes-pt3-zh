# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P17：17_04_05_单元-2-4-算术逻辑单元.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/e1e69186c625923190a7b2e602121bd5_0.png)

In this unit， we're going to talk about a very important component of every general purpose computer called the A L U or the arithmetic logic unit。

Back in 1945， the great mathematician， John Fonneiman。

 wrote a seminal paper in which he included a diagram or a description of how general purpose computers can be built。

And this became to be known over the years as the Phnoman architecture。 Now。

 when you look at this diagram， you see that one key player in the diagram is the central processing unit。

 And within this CPU Yet another important piece is the L or the arithmetic logic unit。 Now。

 if we abstract away all these details and focus only on the LU。

 we can think of an abstraction which receives to multi bit inputs， we call them input 1 and input 2。

 And the third input is the function that has to be computed。

 So the L computes the function and outcomes the result of this computation。Now， the function F。

Is one out of a family of predetermined functions that taken together define what this Alu is capable of doing。

 Some of these functions are arithmetic and some of these function functions are logical。 So。

 for example， common computations that as typically perform our integer addition。

 integer multiplication， Integer division， there may be some logical operations like bitwise N。

 bitwise or and so on。 So there's a really interesting question。

 which is when you set out to build an A， How much functionality do you want to to build in this in this hardware device。

 Well， this is a classical hardware software tradeoff question。

 because if you choose not to implement something in hardware。

 you can always augment it later with software。 So if， for some reason。

 you decide that the AO will not include a multiplication or division。

 presumably at a later point when。You build your software layer。 will。

 You will complete this functionality with software。Alright。 now， so far。

 everything that we said was true for every Alu out there on any computer。 From now on。

 we are going to focus on one specific example of an AU。

 We call it the heck Alu because this is the AU that will hum in the inside our hec computer。

This is the overall gay diagram。 And as we see， the L U has 216 B data inputs， which we call X and Y。

 It outputs a single 16 B output， which we call out。

Which function to compute is determined by6 control bits that have strange names like Z X and N X and so on。

 We will explain these names in just a few minutes。 And based on these six control bits。

 the A U computes one out of the following 18 functions of interest。

And I call these functions functions of interest because in principle。

 the Au can compute many more functions， but we've decided to focus on these 18 functions only。 Now。

 some of these functions are very simple， like the constant 01 minus-1 X Y and so on。

 and other functions are more involved and interesting， like x plus y X and Y and so on。 Now。

 as we see from the diagram， the Alu also computes to1 bit control outputs。

 which are called Z R and N G。 the role of these two control bits and the reason for these names will become clear later in the unit。

 Allright， so let's move on and focus on the output of the Llu from one side and the control bits that cause the Au to compute these outputs。

 and they cause it。Using this truth table。 So this truth table gives you a complete functional specification of this Au。

 That is， if you want to compute a certain function。

 you can look it up on the right hand side of the table。

 You can then read off the zeros and ones that correspond to this function。

 You enter these zeros and ones into the control bits and boom using some sort of black magic。

 the AU will compute the desired function。😊，So let me illustrate how the Ao works in， in action。

 And in order to do it， I'm going to use our hardware simulator so we can fire up the simulator。

 We can load the built in Ao chip。 And as a result， we'll get this chip into the HDL window。 And。

Once we do that， notice that we also get some nice Gui。 and indeed。

 some of the built in chips in our simulator have a Gui side effect that helps the user U to understand what goes on inside the respective chip。

 So this is a diagram that we made up to help you keep track of what happens inside the Alu。

 So moving along， we begin testing。 as you can notice we have set the Alu inputs to two values which are 30 and 20。

 And we also set the control bits to 0，0，0，1，1，1， which if you look at the table that I showed you before。

 What they mean is it's a directive that tells the A you compute y minus X。

 So the next thing that we do， is we have to tell the simulator to actually do something。

 And we do it by clicking this calculator icon， and this。😊。

The L U to evaluate the chip logic on the given inputs。 So this is what happens next。

 And then we can inspect the outputs。 And if we do that， indeed。

 we see that the L U came out with what was advertised， which is -10， the result of y- X。

 So it looks like the L U， at least in this example， works well。Alright。

 let me give you a second example， which demonstrates the logical computational capabilities of the A U。

 The first thing that I do is I tell the simulator to revert to working with Boolean formats rather than decimal formats。

 which make it much easier to enter zeros and ones into the various inputs of the A U。

 And that's what we do here。 So I picked up two arbitrary examples of 16 bit zeros and ones values。

 I entered them。 And then I entered also the。The bit the control bit values 0，0，0，0，0，0。

 which happens to be the directive to compute x and y。 Once again， if you look at the true table。

 you will see this this row listed out。 And indeed， after we click the calculator icon。

 which I skipped in this example， we see that the L actually computed a bitwise and operation。

 and the result is the bitwise end of the two given inputs。 So so far。

 it seems like the l is functioning quite well。 At least in these two examples。Alright， Well。

 we didn't say anything about how the Alu actually works。 It everything so far was。

 was kind of magic。 So now is the time to open up the black box and understand how the Alu actually performed this magic。

😊，So once again， this is the gay diagram or the the interface diagram of the A L U。

 And I want to focus on the six control bits and explain the names and the operations of every one of these bits so。

If Z X equals1。What we want to do is set the x input to 0。 So irrespective of what x is。

 it can be 17 or 19 or 5000 of and3 or whatever。 We set it to 0。 That's what we do if Z X is one。

If n x is one， we set the x input to not x。 This is bitwise negation。

 and also notice that these two things happen one after the other。 So， for example。

 if z x equals 1 and n x equals 1， first of all， with0， the x input and then we neg it。

 So we'll get 1，1，1，1，1，1。 if if this is indeed the values of these two control bits。

 the same thing exactly happens with with a y input using the zy andny directives， if you will。Then。

 we have an F bit。If F is one， we compute x plus Y。 If F is 0， we compute X and Y。 Now these are。

The processed X and Y。 So before we do these computations。

 the X and Y's have already undergone these manipulations that we talked about before。

 They became either 0 or ne gator or nothing。 You know， maybe we didn't touch them。

 And then we compute either addition or 16 B ending。Finally， we have the N orbit bit。 If。

 if the N orbit bit is one， we negate the resulting output， the output that we just computed。

 And if N O is 0， we leave it as is。😊，If we do all these operations， one after the other。

 then what comes out is the desired function。And now that you understand this semantics。

 you can actually look at the table and try to convince yourself。

 You can actually prove that this table delivers the required results。

 And I will demonstrate to you how we can do it。 So let's pick up one example。 Let's。

 let's see how the earlier computes not X。So I look up node X in the right hand side。

 I see it right there， and then I look up the binary values of the six control bits。

 and I start simulating on paper what happens inside the AU。So in order to do it。

 I have to come up with some arbitrary examples of x and Y。 So I make up two values。

 and I use 4 bits instead of 16 to make it less tedious。

 So I have these two examples X and Y arbitrarily chosen。 And then I look at the control bits。

 Z X equals 0， and N X equals 0， which means that we don't touch the X input。 We leave it as is。

And then we move on to the Y input and we see that z Y equals1。 So we0， the y input and n equals1。

 So we negate it。 And what we get is the result1，1，1，1。  moving along， F is 0。 And if F is 0。

 we want to compute x and y。 So we compute x and y。 and we get1，1，0，0。 This is a bit wise n。

 And finally， N O is one。 So we negate the result。 and we get 0，0，1，1。 lo and behold，0，0，1。

1 is exactly not of x。 You know， if you look at the original x， which was 1，1，0，0， we got not x。

 So we have proved that this row in the truth table performs as as advertised。 so to speak。😊。

Moving along， we can take another example。 This will be the final example。

 We look at y minus x in arithmetic operation。And once again， we see the the binary values。

 and we begin simulating them。 So once again， we start with two arbitrary examples of x and y。

 I've chosen 2 and 7。 This is arithmetic operation。

 So it's easier to think about it in both in decimal and in binary。 So we have 2 and 7。

 And if everything works well。 we should get the result 5， because y- x 7-2 should give us 5。

 So we see that Z x is 0， and N x is 0。 So we don't touch the x input， It remains as is。

 And moving along， we see that z Y is 0， So we don't touch the y input。 But N Y is 1。

 which means that we have to negate it。 So 0，1，1，1 became1，0，0，0。Moving along。

 we see that f equals one。 So we compute addition。 and if we add up x and y， we get 1，0。

10 N O also equals1。 So we the result and we get 0，1，0，1 and 10。

1 represents 5 which is exactly what we wanted。 So once again。

 you see that the earlier performed as specified。And many of you may still wonder how this magic actually happens。

 You know， we we were told that we have to be that we have to do subtraction and actually we did addition。

 and we got the result that we expected。 Well， we don't want to get too much into it。

 but if you go back and read or look at the units where we discussed the tools complement method you will understand also the internal mechanics here and why everything comes out as expected。

😊，Now as we said earlier in the unit， the LU also computes and outputs to1 bit output control bits and these bits are called Z and NG and the role of these bits is to say something about the main output of the LU denoted out specifically if out equals0。

 the L sets Zr to 1， otherwise Zr becomes zero and if out is negative then Nng equals1。

 otherwise Nng equals0 now you may ask yourself why do we need these two bits。

 well this will become clear when we put together the overall computer architecture in which these two bits play an important role。

I'd like to， to make a few end notes about about the heck value。

 I hope that we convince you that it's a simple concept。 It is。Very elegant。 And surprisingly。

 it's also extremely easy to implement。And let me explain why if you remember what we do with the LU given all these control bits。

 in some cases， we have to set 16 bit value to zeros。Easy。In other cases， we have to set it to one。

 also very easy。In some cases， we have to negate an incoming value。 We've done it before。

 And I think in Project 1， we built a gate that does exactly 16 bit negation。

 And in some other cases， we have to compute either plus or end。

 And these two computations where already are already taken care of using chips that you designed in previous projects。

 So altogether。There's very little to do。 You know， everything was done in one way or another in。

 in by existing chips that you have already developed。So， to sum up。This is Leonardo da Vinci。

 one of the greatest inventors in history。 And Leonardo said that simplicity is the ultimate sophistication。

 And I hope that I convince you that the heck Alu is both simple， but quite sophisticated。😊。

So this has been the unit on the A U。 And this leads up to the next unit in which we will actually get our hands dirty and build exactly one such A U。

 along with some other chips。

![](img/e1e69186c625923190a7b2e602121bd5_2.png)
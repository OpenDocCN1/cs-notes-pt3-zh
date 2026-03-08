# 斯坦福大学【中英⚡代数编码导论｜Introduction to Algebraic Coding Theory】 p01 p0 1 Video 1： Motivation and the basic problem -BV16sRYYTEwg_p1-

Hello and welcome to this introduction to algebraic coding theoryory。In this series of videos。

 we'll give an introduction to coding theory with a focus on algebraic techniques。

Let's start with some motivation for the basic problem that we're going to think about in this course。

Here is the basic problem in codingd theory。We have some message， X of length K。

Think of x as like a bit string of length K that we want to store or transmit or do something like that with。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_1.png)

We're going to encode。In some way。X to get a code word。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_3.png)

C。😡，And let's say that C has length N。And here we think of n as being larger than K。

 So when we do this en codingding， we are adding redundancy to our original data。

The reason that we are adding redundancy is because we expect something bad to happen。

So that's what happens next， something bad。So what is something bad， Well， it depends on the context。

 but think of it as like some of the bits here get corrupted。

 they get flipped or something like that。And what we're left with is a corrupted code word。

Let's call it C Twiddle。And the goal en codingd theory。

Is to come up with a way to define this encoding map。So， that。

Given the corrupted code word C Twiddle， or maybe given some partial access to it。

We can recover X or maybe recover something about it。Now， this basic setup。

Shows up in a lot of different applications。Two prototypical applications are communication and storage。

So let's talk about those now and see how this sort of situation might arise。

To illustrate the example in communication， suppose we have some sender。 Let's call her Alice。

Here she is。 She's very happy。And we have some receiver。 Let's call him Bob。He's also happy。

 and Bob War glasses。And Alice would like to talk to Bob。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_5.png)

But the catch is that there is some noisy channel。

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_7.png)

Between them， so anything that Alice sends to Bob might get corrupted on route。

This might make more sense or be more practically motivated if you replace Alice and Bob with perhaps a cell phone and a cell tower or a satellite and a satellite dish instead of this stick figure and that stick figure。

 But I'm going to stick with stick figures just you know， I just think they're more relatable。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_9.png)

All right， so we've got this sender， Alice and this receiver， Bob， and Alice has some message X。In 0。

1 to decay K that she wants to send to Bob。These are relatable stick figures who communicate to each other in bit strings naturally。

But Alice knows that if she just sends X straight across the channel。

 Bob's not going to be able to figure out what she meant to say。 So first。

 she wants to add some redundancy。 So she's going to encode X as a code word C。Of length， n。

And that's what she's going to send across the channel。Now。

 this noisy channel is going to do whatever corruption is going to do。

 And what Bob hears is C Twiddle， this corrupted code word。And from this corrupted code word。

 Bob wants to figure out what Alice wanted to say。 So he is supposed to come up with X。

So if we had a way to encode a message X as a code word C， like in the previous slide。

 then Alice and Bob could solve their communication problem。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_11.png)

The second prototypical example is storage。So in this example。

 our message X is no longer something that a sender wants to transmit to a receiver。

 but instead a file that we want to store。

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_13.png)

So say here's our file X。And again， let's suppose that it's just a bit string of length K。

And we want to store our file on some storage medium。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_15.png)

Maybe we want to store it on a CD。Or on a hard drive。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_17.png)

Or maybe on a rate array。Or wherever。Okay， no one uses CDs anymore。Let's replace that with S drive。

Pretend that's a thumb drive。And just like with a noisy communication channel。

 all of these storage media are not perfect。 Bad things can happen。 in know。

 disks can degrade in a rate array。 maybe one of the hard drives just spontaneously combusts boom like that。

 I this really high class special effects going on here。 Yeah， there we go。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_19.png)

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_20.png)

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_21.png)

Or maybe with the thumb drive。I don't know， you send it through the laundry or something。

I know that my laundry has fish in it。 don't know about yours。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_23.png)

But in any case， something bad is going to happen。And we don't want to lose our data。

So what are we going to do， Well， instead of storing the file X directly as is， first。

 we're going to encode it。

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_25.png)

Into a code word C。

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_27.png)

En bits。 So we're introducing some redundancy。 and then that code word C is what we're going to store on these devices。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_29.png)

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_30.png)

Then after something bad happens。

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_32.png)

Let's say to this hard disk。We're going to read。The corrupted code word C twittle。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_34.png)

And ideally， we'd be able to recover our original data from that。 We don't want to have lost data。

 even if something a little bit bad happened。

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_36.png)

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_37.png)

So storage is another place where this paradigm of encode， something bad happens。

 try to recover the original data shows up。

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_39.png)

Communication and storage are only two examples where this type of thing shows up。

 this shows up all over the place across computer science， engineering， mathematics， and so on。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_41.png)

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_42.png)

And we'll see many examples of applications throughout this course。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_44.png)

But first。Let's focus on the things that we care about about such an encoding scheme。

 what do we want from such an encoding scheme。😡。

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_46.png)

Here are four things we might care about。First， we care about handling something bad。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_48.png)

Whatever that may be。Second。

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_50.png)

We care about recovering what we want to know about X。The third thing we care about。

Is minimizing overhead。

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_52.png)

For us， that's always going to mean wanting to maximize the quantity K divided by n。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_54.png)

Remember， K is the length of our message。

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_56.png)

And N is the length of the thing that we eventually are going to store or send。😡。

So if n is not much bigger than K， meaning that this quantity is pretty close to one。

 that this quantity is large。That means that we don't have a lot of overhead。

 We're not storing or sending that much more than we actually wanted to send or store in the absence of anything bad happening。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_58.png)

On the other hand， if this quantity is really small， close to 0。

 That means that we are storing or sending much more than we originally wanted to store a extend。

 that's a lot of overhead。

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_60.png)

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_61.png)

So what we want to do is minimize overhead that is maximize this quantity。

 get it as close to one as we possibly can。

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_63.png)

The fourth thing we care about。

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_65.png)

Is doing all of this efficiently。For example， maybe we want the encoding map。

 which takes X to C or the decoding map， which takes C twiddle to X to be able to run efficiently or something like that。

So given these four things that we care about， the question。Or really the family of questions。

That we're going to be addressing for the rest of this course， basically。

 is what are the best trade offs between these things？



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_67.png)

![](img/4f1c76e21b52d5bd48a2118ef3b08f79_68.png)

For example， it's hopefully plausible that if we really。

 really minimize overhead so we don't add a lot of redundancy。

 it's going to be a lot harder to protect ourselves to get something bad and recover the information that we want about X。

So there's a trade off there。The reason that I said that this is a family of questions rather than a single question is because I haven't really defined what these things are。

That is。What does something bad mean？Is it。That some fraction of the symbols are going to get corrupted。

 Is it that some of them are going to drop out， Is it something else。

I also haven't said what sort of information we want about X？

Do we want to recover all of x or maybe just the first bit of x or something else？Okay。

 I think I said what overhead means， it means this。But I also didn't say what efficiently means。

In particular， what sort of access do we have to the corrupted codeword C Twiddle。

 how much does that access cost and what sort of computational resources do we have to manipulate the information that we get？

There are lots of different ways to define these things。

 and those lead to lots of different and all really interesting questions about these trade offs。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_70.png)

In the next short video， we'll give some formal definitions which provide one way to define these things and give one sort of question here that we're going to study for a little while。

 But there are lots and lots of different ways to do this。

 And we might encounter others of those as we keep going on in the course。



![](img/4f1c76e21b52d5bd48a2118ef3b08f79_72.png)
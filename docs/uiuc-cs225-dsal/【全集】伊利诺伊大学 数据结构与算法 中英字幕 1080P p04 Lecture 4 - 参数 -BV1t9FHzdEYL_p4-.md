# 【全集】伊利诺伊大学 数据结构与算法 中英字幕 1080P p04 Lecture 4 - 参数 -BV1t9FHzdEYL_p4-

Okay。U。So welcome back to CS225。 We are going to finish up with one thing we did not talk about on on。



![](img/96def365bcdb88c79d8cca26a613f02e_1.png)

Heat memory。 And if he looked ahead。You would see that there were some other puzzles and this puzzle。

 I bet a lot of you could figure out what was happening。But we hadn't actually presented the syntax。

 so I want to talk about it。So let's see what do we think is happening on line8？So on line eight。

We do something that looks similar。But I'm using these square brackets， right， So we saw new before。

But this time， I'm also giving a square bracket。 So， yeah。

 it's making an array because square brackets are kind of the universal。



![](img/96def365bcdb88c79d8cca26a613f02e_3.png)

Thing for arrays， we've seen this in almost every language we've done。 And so this is creating。

In why is it？

![](img/96def365bcdb88c79d8cca26a613f02e_5.png)

I'll say allocating。Ting。Memory。For size。Ints。And。Initializing them。Lam。And。Returning a pointer。Okay。

 so we have now created a C++ dynamic array。😡，That we're calling X。



![](img/96def365bcdb88c79d8cca26a613f02e_7.png)

We see it being used in line 11 using the sort of standard notation that we would expect。

And there's one other funny bit of notation， right， Any time we do new。

 we have to have a matching delete。 right， We've said that before。But here we have。

Square brackets that are empty， so it's delete。And this can be read as delete Ar。X。Right？

Why do we call x dynamic Because it that's a very good question。

 It size was not fixed at compile time。 I mean， here it was because。Of in line six， we set it。

 we didn't have user input， but it's dynamic because when executing line eight。



![](img/96def365bcdb88c79d8cca26a613f02e_9.png)

Um， it， it doesn't know how big it is， so you could choose， we could have get input。Input。



![](img/96def365bcdb88c79d8cca26a613f02e_11.png)

Four size and then allocate whatever size， so that makes it dynamic that every time I run the program。

 it could potentially be different。

![](img/96def365bcdb88c79d8cca26a613f02e_13.png)

![](img/96def365bcdb88c79d8cca26a613f02e_14.png)

So can you delete only one element to the array， no， what you can do is cause an error。😡。

If we put empty brackets here， if I didn't have size， it would be a compile error。Om。



![](img/96def365bcdb88c79d8cca26a613f02e_16.png)

Can you change this size later on， Well， I could delete this one and allocate a new one。

 C plus plus new does not have a way to extend。A new remember from Monday was how we allocated memory on the heap。



![](img/96def365bcdb88c79d8cca26a613f02e_18.png)

So， but let's talk about the delete here。Any time we say new， we have to have a matching delete。

 Any time we say new。We have to have with square brackets。

 we have to have a delete that matches with square brackets， why？



![](img/96def365bcdb88c79d8cca26a613f02e_20.png)

So。Because that's telling it that I need to destruct all of the objects instead of just one。



![](img/96def365bcdb88c79d8cca26a613f02e_22.png)

So if I wrote delete。😡，And didn't have that。 What would happen is it would deallocate all the memory。

 but it would not call the destructor for all of the objects。 And this is never what you want to do。



![](img/96def365bcdb88c79d8cca26a613f02e_24.png)

So let's see if x is a pointer Y doesn't it store an address， it does store an address。



![](img/96def365bcdb88c79d8cca26a613f02e_26.png)

In fact， what it stores is if imagine here is memory， and I'm going to write it horizontally。

 so this is going larger。 Here are my integers in memory。



![](img/96def365bcdb88c79d8cca26a613f02e_28.png)

It stores this address。And square brackets。Is a dereference operation。

 So the first square bracket with0 says go0 spaces beyond the starting。Aress， if I give it one。

 it says go one space beyond the starting address。Would it cause memory leakage if you did not have the square brackets。

I cannot easily answer that question。If you do not have the square brackets， what will happen is。

It will still deallocate the memory， but it won't call the destructor。

Since it doesn't call the destructor。Those objects might have their own allocated memory。

 so it could cause memory allocation， memory leakage。



![](img/96def365bcdb88c79d8cca26a613f02e_30.png)

![](img/96def365bcdb88c79d8cca26a613f02e_31.png)

If those objects were like ints and there's no real work to do in the deor。It wouldn't matter。



![](img/96def365bcdb88c79d8cca26a613f02e_33.png)

Yeah， so delete FTP array would delocate all the memory for the FTP connections。

 but would not close them， that's a very good example。



![](img/96def365bcdb88c79d8cca26a613f02e_35.png)

No， you just have to read when this line runs as long as size has a value。

 that's how big it'll allocate。What happens in line 5， what is the context of x？



![](img/96def365bcdb88c79d8cca26a613f02e_37.png)

X is a pointer to an int because the way we store an array is by storing the address of its start。



![](img/96def365bcdb88c79d8cca26a613f02e_39.png)

Okay。So right an array is， and in fact， even if I had a non dynamic array。

 what really it stores what that variable has in it is the address of the start of the array。Okay。

How often are we going to do this well， in 225， like twice。

 maybe almost always you can use other tools in C++ for allocating this kind of stuff。Right。

 x is the array you would probably need to be returning its size because the array does not know its size。



![](img/96def365bcdb88c79d8cca26a613f02e_41.png)

![](img/96def365bcdb88c79d8cca26a613f02e_42.png)

It is absolutely true that the kinds of bugs we can get in C plus plus for not handling memory are some of the most hair tearing bugs that exist。

 And that's why so many languages have moved to things like garbage collection。

 It really does remove a whole category of hard to debug bugs。



![](img/96def365bcdb88c79d8cca26a613f02e_44.png)

But in general， there is still some level that this stuff needs to be handled。

 Part of why we do this in 225 this way is。

![](img/96def365bcdb88c79d8cca26a613f02e_46.png)

Even in those garbage collected languages， there's a need to be thinking about the lifetime of memory。



![](img/96def365bcdb88c79d8cca26a613f02e_48.png)

Because that still impacts performance of a program and by forcing you to think about it explicitly。

 it can help you develop those instincts。So any time we have a new initialized as an array with square brackets。

 we need to match it with a delete with square brackets， absolutely。I mean。

If you had an array of pointers and you initialized each of those pointers。

 you would have to delete each of those pointers explicitly， yes。

If that's the question you are asking。Every every call to new must have a matching call to delete。😡。

Just it's right， this is， this is， you had to in chemistry balance electrons and electrons and math。

 the numbers the values had to add up well in。C plus plus every new must have a matching delete。

What is the purpose of deletete， Delete， just like always。

Deep destructs the objects and releases the memory so it can be reused。

 If you don't release the memory， you're saying。I still need this memory forever。

Delete will always take an address， and it will always take an address。

That was allocated by a call to new。Well， you can create an array of integers without using new。

 but you cannot create a dynamic one or one you return。Does new return avoid pointer。

 No new returns a pointer of the type？

![](img/96def365bcdb88c79d8cca26a613f02e_50.png)

That is allocated。 So in this case， new is returning an inch pointer if I did new。Cube。



![](img/96def365bcdb88c79d8cca26a613f02e_52.png)

I'm returning a cube pointer。Okay。The correct delete should have square brackets。

In this particular case， it will not cause a bug if it does not。

But you should always match the delete type with the matching delete type。Okay。

So that's the last bit of heat memory allocation。Dynamic means determined at runden time。Okay。So。

We have talked about three ways of talking about memory。And talking about variables。

 we've talked about variables。We've talked about reference variables that are names。

And we have talked about pointers。Which are just variables， but that store addresses of things。So。

They don't seem that useful。 So far， we've seen， well。Another name。Name。For something。

But that's really all we've seen that a reference does。Here we have handle。Heap memory。And also。

 kind of。Another。Way of accessing something。A variable。So。We have all of these kinds of things。And。

Why。Well。We have one critical need for。A pointer。But we haven't really seen a critical use case for a reference。

 We've used it in this weird case that you saw with pixels that when you did get pixel。

 you'd be returned a reference， and you could modify that。



![](img/96def365bcdb88c79d8cca26a613f02e_54.png)

![](img/96def365bcdb88c79d8cca26a613f02e_55.png)

![](img/96def365bcdb88c79d8cca26a613f02e_56.png)

But let's talk about it in a little bit more。Let's talk about calling functions。

 We've all called functions in all sorts of languages。

 and you've already written function calls in C plus plus。So here。We are going to look at。

Calling functions。And we're first going to look at by value。

 which is actually sort of the normal model， right， So what happens here， let's see。Here。

 we're leaking memory， but we don't care about that right now。



![](img/96def365bcdb88c79d8cca26a613f02e_58.png)

So here we create a， let's walk through what this program does。 It's going to take two cubes。

It's going to create a new cube。

![](img/96def365bcdb88c79d8cca26a613f02e_60.png)

By sort of pushing those two cubes into a bigger one， right。

 we can see that what we do is we get the volume of one cube and the volume of other cube。

 and then we create a cube that has the same volume。



![](img/96def365bcdb88c79d8cca26a613f02e_62.png)

![](img/96def365bcdb88c79d8cca26a613f02e_63.png)

Okay。Well， let's look at this。So if our join cubes function takes by value， what happens？

We start with。Let us see。 We have C1， so we have a variable C1。That is a pointer。

 and it is initialized， and this is going to be this stack。And this is going to be the heap。

It is initialized pointing to a cube。Up here。4。Right。So that's what happens in line 29 in line 30。

 we have C2， which is also on the stack。

![](img/96def365bcdb88c79d8cca26a613f02e_65.png)

And it is initialized pointing2。A newly allocated cube。We'll walk through all the steps here。

They just got a size five， okay。We go to line 32， we create another cube。

This time we are going to try to create a cube， right？

And we' are going to create it by initializing it to the value of this function。So what do we do。

 Let's see， we do star C1。哦。What is star C1 going to be？C1 is a pointer。Yeah。

 so it's the actual object。 So it's that cube of four。

 and what's going to happen is it's going to produce。It's going to become that value。

 and we are calling by value whenever we call a function by value， which is the normal way。

 what we do is we make a copy。So we make a copy of that cube。Okay， and then we make a copy of C2。



![](img/96def365bcdb88c79d8cca26a613f02e_67.png)

Which is the actual cube that is five， this is the four， this is the five。ok。Those are on the stack。

 somewhere。Okay。Then on the stack， we make a volume that we initialize with get volume， right？



![](img/96def365bcdb88c79d8cca26a613f02e_69.png)

So we get 64 here gets returned。And 128， 125， if I could do math。Right。We good。

189 is stored in total volume。Yep。I could not do dot on the pointer directly， but I'm not。

 I don't have a pointer right， This is C1 in my join cubes function is a cube。

 not a pointer to a cube。😡，Because I use the star operator right to dereference the pointer to the cube。

And。Power is a power function。It is in it takes the power， right， so it's this to the that。Rightai。

Okay， so then we compute our total memory。And we get 5。74。Gets us our。Cub root of 1，89。



![](img/96def365bcdb88c79d8cca26a613f02e_71.png)

Now we create a new cube here， right， we're going to call this result。



![](img/96def365bcdb88c79d8cca26a613f02e_73.png)

And it is 5。74。Why it is the parameter in join cubes become cube and not cube star。No。

I wish I could claim I could do cube roots in my head， I can read my notes。Notes are your friend。Um。

 but there's a， there's a better question here， why does the premium So right here， C1。



![](img/96def365bcdb88c79d8cca26a613f02e_75.png)

![](img/96def365bcdb88c79d8cca26a613f02e_76.png)

In the main function。Becomes a cube by dereferencing。And we make a copy of that cube into C1。

Since these are copies they take up memory， absolutely they do。

They are taking up memory on the stack as soon as we make this copy。We use up some memory。By line 16。

 there are four total cubes。 I agree。 there are two cubes on the stack in mainine。

 and there are two cubes on the stack in join cubes。Yep。It can be。 And we'll。

 we'll talk about the overhead of why we might not want to do this。 So， and then we return result。

 which， and I'm going to stick with how to think about this might work is going to take oops。



![](img/96def365bcdb88c79d8cca26a613f02e_78.png)

I hate it when it does though， okay。Um， iss going to actually make this whole thing is now going to get。

The copy of 5。74。Okay。What if you， we're going talk about other ways to do this。C 3 is on the stack。

Um， absolutelybs。And C3 is now going to be initialized by copying that return value。It's returned。

When you return from a function， you copy it out of that function into the collar。😡。

when I return something， I am as a function handing off that value to whoever called me。



![](img/96def365bcdb88c79d8cca26a613f02e_80.png)

If I did return of Ampersand results， I would return a name of the result inside me that no longer existed。

 right？

![](img/96def365bcdb88c79d8cca26a613f02e_82.png)

So。Do we need delete C 1 and C 2， Ab， we should be。Lak memory。4。C 1 and C2 right there。Okay。

 so let's walk through what happens in the most。Primitive view of this。At this point， when we return。

 this goes away。Okay， we created a cube， we created a cube。Wei。

Create a cube in line 15 and twice for each of those D references。So we have one，2，3， four，5。



![](img/96def365bcdb88c79d8cca26a613f02e_84.png)

6ix， seven potential cubes exist over the life of this program。After it is， the function exits。

 all the variables go away。

![](img/96def365bcdb88c79d8cca26a613f02e_86.png)

Okay， we're going to talk about leaking memory in a couple of ways that when my program exits。

 the operating system cleans up all the memory。

![](img/96def365bcdb88c79d8cca26a613f02e_88.png)

![](img/96def365bcdb88c79d8cca26a613f02e_89.png)

When I return from Maine， there's some stuff that happens before that。

 And so we're going to talk about。Contex also。

![](img/96def365bcdb88c79d8cca26a613f02e_91.png)

Yeah，4 is the length of a side of a cube。

![](img/96def365bcdb88c79d8cca26a613f02e_93.png)

Okay， so I will argue we create a cube here， create a cube here。



![](img/96def365bcdb88c79d8cca26a613f02e_95.png)

Let's change colors if I can get this thing to play nicely。Want to do。Okay。

 so here is a cube creation。Here is a cube creation。Okay。

Here is a cube creation and here is a cube creation。Here is a cube creation。Here is a cube creation。

And finally， here is a cube creation。Are all the potential times we made cubes。ok。Yeah， I。

Somehow overwhelmed the poor little computer。So。Okay。So。Here we are calling。Different constructors。

 potentially。Okay。If you run this code。You're gonna see less than that。W。

Why do we use these as pointers because it'll work better for future examples？



![](img/96def365bcdb88c79d8cca26a613f02e_97.png)

This is toy code that exists entirely to show different ideas。

I wanted the main function to be as closely as possible。So what all happens。

 because is these red dots are sort of conceptually what happens。



![](img/96def365bcdb88c79d8cca26a613f02e_99.png)

![](img/96def365bcdb88c79d8cca26a613f02e_100.png)

But it turns out。You。Are allowed。2u。😔，The compiler is smarter than that。Yeah， so。

This tube has to be created， so that's real。

![](img/96def365bcdb88c79d8cca26a613f02e_102.png)

And this cube has to be created。 The two calls to new， right， Those have to happen。



![](img/96def365bcdb88c79d8cca26a613f02e_104.png)

Okay， this cube， I I guess I'm going to draw boxes around the red dots that have to happen。

And this cube。Have to happen。Those have to be done because you're promising by calling by value that if Jo cubes mucks with the cube。

 it does not change the cube outside。Okay。What else has to happen， this cube has to happen。Okay。

 because we are creating a new cube of a size that we didn't have before。It turns out。The last two。

Don't。That the compiler can be smart and realize that instead of creating。

The cube on line 20 in the place for the function， it can create that cube in the return location。



![](img/96def365bcdb88c79d8cca26a613f02e_106.png)

Okay。And in line 32。

![](img/96def365bcdb88c79d8cca26a613f02e_108.png)

So this cube can be created where it's returning。And on the return。



![](img/96def365bcdb88c79d8cca26a613f02e_110.png)

At line 32， instead of creating C3 as a default cube and then updating its value。

 the compiler can say， hey。I bet。I can， instead， just。

Create it in the place where I'm going to keep C3。So five sort of have to happen。

But two of them dealt。29 and 30 are not quite the same because one takes cube4 and one caps cube5。

 but they're the same kind of call。

![](img/96def365bcdb88c79d8cca26a613f02e_112.png)

Okay， we're not going to ask you subtle questions about this， but it it if。

If you want to see what happens。Um， actually， even on dash00， all of these go away。



![](img/96def365bcdb88c79d8cca26a613f02e_114.png)

So we get five， even with no optimizations because this is a language level optimization。So。



![](img/96def365bcdb88c79d8cca26a613f02e_116.png)

Now， if a compiler is really smart， it might be able to avoid the creations on line 15。

 because it could figure out that inside join cubes。

 we don't actually modify the cube and hence use it。

 but in practice it's probably going to make those copies。😡。



![](img/96def365bcdb88c79d8cca26a613f02e_118.png)

Okay。So that's how it works by value。Line 32 is not necessary。 Line 32 is necessary。 How would it。

Well， the copy is on line 32， the code is needed， but that code is the creations don't have to happen。

 right， because it can be really smart and make the creation on line 20 happen in the place where C3 is going to be。

😡。

![](img/96def365bcdb88c79d8cca26a613f02e_120.png)

![](img/96def365bcdb88c79d8cca26a613f02e_121.png)

Does that make sense。That if the compiler knows that the return of this function is going to go where C3 is and the compiler in join cubes knows that this cube that's creating is going to be returned。

 it can avoid those。

![](img/96def365bcdb88c79d8cca26a613f02e_123.png)

![](img/96def365bcdb88c79d8cca26a613f02e_124.png)

We will get to Kst in a moment。In line 15， I am creating copies of the cubes that C1 and C2。2。

 absolutely。Okay， so this was by value。 We had allocated the cubes as pointers， but。



![](img/96def365bcdb88c79d8cca26a613f02e_126.png)

We return them by value。

![](img/96def365bcdb88c79d8cca26a613f02e_128.png)

It turns out that the one that will be created is the one in line 20， but。That's it。Okay。Now。

 what if we wanted to call using pointers？Okay if we wanted to call using pointers。Our main program。

 What have we changed？ Well， everything up until line 32 is identical， correctect。

 does exactly the same thing。But here， instead of having to dereence C1 and C2。

So let's walk what happens right here， we create a pointer。It points to a cube。

And here we create a pointer and it points to a cube。Okay。Now we call join cubes。

 and we call this call by pointer。😡，But really， is this a call by pointer。

 This is just called by value， right。

![](img/96def365bcdb88c79d8cca26a613f02e_130.png)

It's just that the value。Happens to be a pointer。Okay。If the value is a pointer。

 what are we going to do， We're going to copy C1。Which is a pointer。And it's going to be a copy。

 So it's going to point there。 And we're going to copy C2。Which is a pointer。

And it's going to point there。So we've only made two cubes， whereas we made four cubes before。

 and what we copied instead of copying the cube。

![](img/96def365bcdb88c79d8cca26a613f02e_132.png)

We copied the pointer。Then we do get volume in all this， and here we create a cube。And we return it。

So here。We have avoided copying those cubes。And instead， just copied pointers。

Conceptually we have these cubes， and there we go。Yep， that's why up here in our join cubes。

 Jo cubes has。

![](img/96def365bcdb88c79d8cca26a613f02e_134.png)

Pointers， so to accept to call the methods， we have to use the arrows operator。Well。

 there's space efficiency， but there's also presumably。OcPerformance speed efficiency。

Could we use a reference？ Have you looked at my next slide。So these again， probably don't happen。So。

We will talk。Right， we could， if C1 was a cube， we could use Ampersan to get the address。



![](img/96def365bcdb88c79d8cca26a613f02e_136.png)

Well， in this case， we wrote it as pointers because we wanted to see how pointers work。



![](img/96def365bcdb88c79d8cca26a613f02e_138.png)

How would I put C 3 on the heap。U by。

![](img/96def365bcdb88c79d8cca26a613f02e_140.png)

Doing new and getting size， I mean， to make anything on the heap， you have to do it with size。Um。

 we still have the problem of needing delete。

![](img/96def365bcdb88c79d8cca26a613f02e_142.png)

C1。

![](img/96def365bcdb88c79d8cca26a613f02e_144.png)

Deelete。C2， But if we did that， there would be no memory leaking。

We are saving memory and we are saving time， potentially。Um， this will make in practice three cubes。

 right， one cube gets made here， one cube gets made here and one cube gets made here。Absolutely。

Pass by value makes a copy of the thing。Pass by pointer makes a copy of the pointer。

Here's a really good question。 If we modify C1 and C2， do we modify the original。 So， yeah。

 if I did C1 arrows set length。

![](img/96def365bcdb88c79d8cca26a613f02e_146.png)

To10。I would change this to 10。Isn't Jo Cus call taking references， No， it's taking pointers here。

Is there any downside of passing to pointers well？

![](img/96def365bcdb88c79d8cca26a613f02e_148.png)

By passing a pointer。If I was a malicious programmer in writing the Jo cubes function。

 I could modify C1， which you probably didn't want it to do。Delete takes a single argument。

 so you cannot do it all in one line。Right， the the good thing about passing a pointer is it's fast。

 Well we'll get to this in the summary， Why are the cubes not created at line 32 in this case。

 same reason as last time that in line 20， it puts it here。



![](img/96def365bcdb88c79d8cca26a613f02e_150.png)

![](img/96def365bcdb88c79d8cca26a613f02e_151.png)

And then in line 32， it decides that there is here。I mean， C1 arrows is going to look at a。I mean。

 we use the arrows operator。C1arrows get volume is going to call get volume。

 assuming C1 is a pointer on C1 C1。 get volume is going to call C1 get volumee on C1 if C1 is an object。



![](img/96def365bcdb88c79d8cca26a613f02e_153.png)

![](img/96def365bcdb88c79d8cca26a613f02e_154.png)

We will get to Cons。This optimization isn't really important， but the return value。

It knows where it's going to put the return。 So instead of creating it locally and then copying where it hands it back。

 let me imagine this if I was a factory。

![](img/96def365bcdb88c79d8cca26a613f02e_156.png)

If I was really smart， I could make my factory be right at your house。That would be really cool。

 right， if my factory was right at your house but didn't take up any space。

 I could just when you order a book， have it appear in your house。

 because my factory is in your house。 Well， one of the nice things about a computer is physical space doesn't work out the same way。

 So my function can just have the place it creates the book you order be in your house。

 And then you can just say， h， how about if when I set up where books are delivered。

 I have them be my bookshelf。 So when I call。😊。

![](img/96def365bcdb88c79d8cca26a613f02e_158.png)

![](img/96def365bcdb88c79d8cca26a613f02e_159.png)

![](img/96def365bcdb88c79d8cca26a613f02e_160.png)

![](img/96def365bcdb88c79d8cca26a613f02e_161.png)

Get a book， the factory immediately creates it in my bookshelf， and we don't have to copy。



![](img/96def365bcdb88c79d8cca26a613f02e_163.png)

Nothing， there is no difference between doing these on two lines and one line that the compiler。

Here's it out。

![](img/96def365bcdb88c79d8cca26a613f02e_165.png)

The method here doesn't want objects， right， here， the method wants pointers。



![](img/96def365bcdb88c79d8cca26a613f02e_167.png)

Okay。So call by pointer， we copy the pointer in。Call by value， we copy the object in。



![](img/96def365bcdb88c79d8cca26a613f02e_169.png)

So then there's references， which is the one thing we haven't figured out a real use for。



![](img/96def365bcdb88c79d8cca26a613f02e_171.png)

Well with a reference， what do we do With a reference， well。This looks here， if we look at this。

 the code in main is identical to the code we had in Ma for value。



![](img/96def365bcdb88c79d8cca26a613f02e_173.png)

![](img/96def365bcdb88c79d8cca26a613f02e_174.png)

There's no difference。The code in。Join cubes has one difference， and here it is。There it is。

 it says that C1 and C2 are references。So what does that mean？Well。

It means what we're going to do is create a pointer here and a pointer here。And I'm drawing。

 this is how I'm going to differentiate between pointers and references。 So we create the new。

 We create these two cubes。

![](img/96def365bcdb88c79d8cca26a613f02e_176.png)

Here we dereence C1。 So that is the box。 This is that box。 right， that cube。

 And here what we're going to do is C1。 and I didn't draw。A box and C2。 And I didn't draw a box。

They are just names。4。Those boxes。Okay。So this works a lot like the pointer solution。

But I don't have to use the arrows operator。Right。So it's very fast。

It's potentially faster than pointers。In some cases， you can。Do tricks where nothing gets copied？

That's sort of neat。That in call by reference， potentially， there are no copies made。Okay。

Everything else works the same。This is exactly like by value except the arguments are references。

 so when you pass by reference， it's the variables getting passed absolutely。

What is the benefit of passing by pointer versus passing by reference？Om。

They are doing different things。 Pointiners have somewhat more power of that。 They can。

How be changed。They can。Be copied。Things like that。A reference， when I create it。

 I can never change it， a pointer I can change。 a reference when I create it。

 I can't really make a copy of it the same way。 I can't store it as easily。😡。



![](img/96def365bcdb88c79d8cca26a613f02e_178.png)

So nothing copies here when calling the function。 The right way to think about it is that。



![](img/96def365bcdb88c79d8cca26a613f02e_180.png)

The whatever magic happens is that C 1 and C2 inside the function have the name of。C1 and C2。

Outside the function。8。When we pass pointers， we take exactly the space of a pointer when we pass by reference。



![](img/96def365bcdb88c79d8cca26a613f02e_182.png)

We don't know how it works。Really。The right way to think of it is a reference is just another name。

Yes， if if again， if I did C1 dot set。Length。To 10。

 I would be changing this guy to have a length of 10。Yeah， references can't be known。

 Refs have to exist。When you create the reference， you must initialize it。References。A connected。

 in a sense， references are the initial object。嗯。Cube reference C1 equals new cube would be an error。

Um because。C1 is then a reference to a cube， not a pointer to a cube， but new returns a pointer。

The what the reference refers to can be changed， but the reference cannot be changed。

The difference between pass by value and pass by reference。 So it's another name， right。

 We've said that this thing is called C1， and this thing is called C2。Okay。



![](img/96def365bcdb88c79d8cca26a613f02e_184.png)

Let's walk through。What is copied when this function is invoked。 So this is a simplified one。

 If I have a function fo and I call by value。

![](img/96def365bcdb88c79d8cca26a613f02e_186.png)

What do we call up， We'll get to constant。If we can get through。

So we here we make a copy of the cube。Cube is copied。 What is copied here is a memory。Adds。

Or a cube pointer。What is copied the name？And I'm using the name here and not talking about what it。

Does。Because how it's implemented isn't important to us。You can。

Does modifications pass in modify the object？😡，No， right。

 because we've made a copy if in our function， we modified the cube。

 it will not modify the outside cube。Yes。If the reference。

Let's say by star right when we dereence the pointer， we are talking about the same object。

 so we modify it。And yes。Is there always a valid object passed in by value， yes。

 we always have an object。

![](img/96def365bcdb88c79d8cca26a613f02e_188.png)

That is to say， we always have space。No。That。I can have a perfectly valid pointer that points to something like noll。

So， no。

![](img/96def365bcdb88c79d8cca26a613f02e_190.png)

By reference， yes。Yes， we always have a valid object。Speed。Possibly。Slow。By value。

 imagine if what I was copying by value was a PNG。I was copying the P G。That could be huge， right。

 think of your images。By pointers。Fast。No more。Then one address。That I only copy an address。

By reference。Fast。And the secret is。No more。One address。Under the hood， in most cases。

 a reference will be implemented with a pointer that is hidden from you， the programmer。What's safe。

 And what do I mean by safe。 Sa is， it always exists and safe is， I can't screw things up。

 So what do I like， I like by value。 It's nice and safe。

I don't like by pointer from a safety perspective because I break things。By reference。Kina。

It's kind of safe。Because。I am guaranteed to have an object with a reference， but。

I can also change what was called。Okay。That's it， I had hoped to get to Ks today。



![](img/96def365bcdb88c79d8cca26a613f02e_192.png)

But it turns out we have a way to fix this。 And， yes， it is a contrafe。

And I will talk about that on Friday because there's some problems we're going to see when we use it。

 but a constr is a very helpful tool。

![](img/96def365bcdb88c79d8cca26a613f02e_194.png)

Thank you everyone。Safety is based on really。These two are the things that I'm talking about for safety is modified by the does it modify the colors's object and is there always a valid one？



![](img/96def365bcdb88c79d8cca26a613f02e_196.png)
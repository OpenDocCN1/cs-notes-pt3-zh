# 【全集】伊利诺伊大学 数据结构与算法 中英字幕 1080P p03 Lecture 3 - 堆内存 -BV1t9FHzdEYL_p3-

Okay。Will we be teaching you how to write tests， not explicitly。

 we've given you a bunch of code and you can write tests from code。

 we aren't looking for formal tasks。

![](img/36947c91fbde9e9ddb3e92988d111608_1.png)

![](img/36947c91fbde9e9ddb3e92988d111608_2.png)

More discussions on Broadway， I recommend posting in Piazza or sticking around after and I'll answer questions。

 but we need to start the new material today。Okay。Okay。

So today we're going to wrap up what we were talking about， which yesterday。

 which was stack memory and move on to the idea of heat memory。



![](img/36947c91fbde9e9ddb3e92988d111608_4.png)

![](img/36947c91fbde9e9ddb3e92988d111608_5.png)

So if yesterday， Friday， you know， the only days that happen are when I lecture。

 So stack memory was what we talked about on Friday and stack memory is where stack frames。Fras。

Of function calls。Os。Go。So every time you call function there will be what's called a stack frame that'll have the variables and you add variables。

 and then when you return you will clean them up。

![](img/36947c91fbde9e9ddb3e92988d111608_7.png)

![](img/36947c91fbde9e9ddb3e92988d111608_8.png)

Um， what is the addressability of this memory we don't know？That that's not important to us。



![](img/36947c91fbde9e9ddb3e92988d111608_10.png)

We're only going to talk about memory in this lowest level for a short while because the addressability and questions like that are going to depend on the hardware and C++ as a language is not hardware specific so you would have to look at your own hardware to determine none of that level well we are being fairly low level in this course。

 none of that level is going to be of importance to us in this class I will say that every modern architecture you deal with is byte addressable so on the eight bits。

😡。

![](img/36947c91fbde9e9ddb3e92988d111608_12.png)

![](img/36947c91fbde9e9ddb3e92988d111608_13.png)

![](img/36947c91fbde9e9ddb3e92988d111608_14.png)

![](img/36947c91fbde9e9ddb3e92988d111608_15.png)

![](img/36947c91fbde9e9ddb3e92988d111608_16.png)

So the stacks go on and are automatically can。Trolled， right， we go down， grow。Ws down。Okay。

And at the end， I pointed you and asked you if you had chime to take a look at what I called a puzzle。

 so let's look at this puzzle。

![](img/36947c91fbde9e9ddb3e92988d111608_18.png)

So on the right here， I've got a chunk of code， this is a little program that uses our cubeB class。

And。Does anyone see something that is wrong with it？



![](img/36947c91fbde9e9ddb3e92988d111608_20.png)

Regular office hours， as was announced， will be starting later this week as opposed to ad hoc office hours。



![](img/36947c91fbde9e9ddb3e92988d111608_22.png)

Okay。

![](img/36947c91fbde9e9ddb3e92988d111608_24.png)

Returning a pointer to the stack。 Yes， and some other function is in some other code。



![](img/36947c91fbde9e9ddb3e92988d111608_26.png)

![](img/36947c91fbde9e9ddb3e92988d111608_27.png)

I'm not worried about that some other function is defined， but yeah。

 we return a pointer to the stack。

![](img/36947c91fbde9e9ddb3e92988d111608_29.png)

So what happens， let's walk through this code。

![](img/36947c91fbde9e9ddb3e92988d111608_31.png)

Okay， so。We start and this is a C++ program right， so we're starting here on line 9。

 which is the main function。The main function executes and it allocates a pointer。



![](img/36947c91fbde9e9ddb3e92988d111608_33.png)

Right C and we had looked up on Friday and saw that on our machine anyways， pointers were8 bytes。

 and so here is the stack frame for main starts here and it creates a pointer C。



![](img/36947c91fbde9e9ddb3e92988d111608_35.png)

![](img/36947c91fbde9e9ddb3e92988d111608_36.png)

And then it calls。

![](img/36947c91fbde9e9ddb3e92988d111608_38.png)

Create cube， right， So another stack frame goes on， and there's some stuff， which we don't know。



![](img/36947c91fbde9e9ddb3e92988d111608_40.png)

And at some place， what does C cubebe do？Create cube calls a constructor， right？



![](img/36947c91fbde9e9ddb3e92988d111608_42.png)

It calls the constructor and it constructs a cube here。And it calls a custom constructor。

And initializes it to 20。Right。And then it says， okay。We are going to return the address of C。

So yeah， some of you have seen ahead， but let's walk through it。



![](img/36947c91fbde9e9ddb3e92988d111608_44.png)

So the next line we do is return the address of C， so we're wrapping up this function and we're going to put us our return value。

 So what's going to appear here is going to be the address of C， which is the smallest value， so0， F。

 F F， FF。

![](img/36947c91fbde9e9ddb3e92988d111608_46.png)

![](img/36947c91fbde9e9ddb3e92988d111608_47.png)

0ero，0 C。8， and we're going to store that in C。 So right now the contents here。

 and I'm just going to draw a pointer here。Are going to point to。There。So at this point。

Our error has actually happened。But we don't really know it yet。



![](img/36947c91fbde9e9ddb3e92988d111608_49.png)

，There's nothing wrong with storing a nonsense value in C。 We don't crash。

 The system's not going to give us an error。

![](img/36947c91fbde9e9ddb3e92988d111608_51.png)

Because that's how the stack goes。 we talked about it on Friday that the stack grows from a highest value to a smallest value。

Goes from the top of memory down。Okayi。So。We have this pointer， that's okay。



![](img/36947c91fbde9e9ddb3e92988d111608_53.png)

But let's see， then we can do some other function。

![](img/36947c91fbde9e9ddb3e92988d111608_55.png)

U。

![](img/36947c91fbde9e9ddb3e92988d111608_57.png)

So some other function， okay， so we created C。

![](img/36947c91fbde9e9ddb3e92988d111608_59.png)

We've returned。Some other function happens， and some stuff gets written in there。What， I don't know。

 Whatever this other function does， We don't know anything about it。 So he writes some stuff here。



![](img/36947c91fbde9e9ddb3e92988d111608_61.png)

And then what happens on line 12？

![](img/36947c91fbde9e9ddb3e92988d111608_63.png)

Line 12 is where we have a problem。We assume that there's some other stuff in the stack frame so why did it skip two blocks when you actually dig into writing a compiler and doing the lowest level stuff that when you call a function there are things besides variables that end up on the stack but that's a very good question so right so there is stack frame。



![](img/36947c91fbde9e9ddb3e92988d111608_65.png)

![](img/36947c91fbde9e9ddb3e92988d111608_66.png)

![](img/36947c91fbde9e9ddb3e92988d111608_67.png)

![](img/36947c91fbde9e9ddb3e92988d111608_68.png)

Frame。

![](img/36947c91fbde9e9ddb3e92988d111608_70.png)

We don't really care about that because we're not going to watch it。



![](img/36947c91fbde9e9ddb3e92988d111608_72.png)

Why does some other function overwrite the space of C cube because create cube finished， right？



![](img/36947c91fbde9e9ddb3e92988d111608_74.png)

It's blocked back through this。Create cube created the cube。



![](img/36947c91fbde9e9ddb3e92988d111608_76.png)

And then it returned。When it returned， it's gone， right when we leave this function。



![](img/36947c91fbde9e9ddb3e92988d111608_78.png)

That the lifetime of that function ended。 its memory is released。

 and it's released exactly by moving the snack up。

![](img/36947c91fbde9e9ddb3e92988d111608_80.png)

![](img/36947c91fbde9e9ddb3e92988d111608_81.png)

Yeah， I like that。So， the next function comes here。And it writes some stuff。Well now。



![](img/36947c91fbde9e9ddb3e92988d111608_83.png)

What happens？What happens on line 12， on line 12， we create a double。

 so somewhere here we're going to create a double which is going to be8 bytes。



![](img/36947c91fbde9e9ddb3e92988d111608_85.png)

![](img/36947c91fbde9e9ddb3e92988d111608_86.png)

And we're going to call this， let's erase this stuff because we are now back to Maine。

 having returned from some other function。哦。Trying to find where am I。嗯。

I to erase this just to give me some space。So this is now going to be double。Li。

And we're going to initialize it。

![](img/36947c91fbde9e9ddb3e92988d111608_88.png)

We're going to initialize it by a call to get volume。 So what do we do， We follow the pointer。



![](img/36947c91fbde9e9ddb3e92988d111608_90.png)

And say， okay。What we have here。Must be a cube。Well， what is it？



![](img/36947c91fbde9e9ddb3e92988d111608_92.png)

I don't know。Whatever junk， some other function left there。



![](img/36947c91fbde9e9ddb3e92988d111608_94.png)

So what value happens？

![](img/36947c91fbde9e9ddb3e92988d111608_96.png)

The system is going to treat this address as if it's a cube。

And it turns out a cube only has the one value length， and it's going to take the bits。

In these eight bytes。

![](img/36947c91fbde9e9ddb3e92988d111608_98.png)

En treatat them as if they were。A double precision floating point number。And that's it。

Because once we。Return from a function。We。Give up the access to the memory， say it's not yours。



![](img/36947c91fbde9e9ddb3e92988d111608_100.png)

So right， we went through。

![](img/36947c91fbde9e9ddb3e92988d111608_102.png)

We called Cate Cu。 Cre Cube got some memory。

![](img/36947c91fbde9e9ddb3e92988d111608_104.png)

It allocated some memory。 It created the cube。And then， it returned。As it happens。

 because that was automatic， the cube got called a deor， but we haven't talked about those yet。

 That's not important。 but the memory was then released， right？ So nobody owns this memory。

 So right now。Memory released。Wen。Function returns。



![](img/36947c91fbde9e9ddb3e92988d111608_106.png)

This is what has always happened with a function， right， that when you call the function。

 it allocates variables that are local and when it returns。



![](img/36947c91fbde9e9ddb3e92988d111608_108.png)

![](img/36947c91fbde9e9ddb3e92988d111608_109.png)

That memory gets released。This has been true in Java and C++ and everything else。



![](img/36947c91fbde9e9ddb3e92988d111608_111.png)

You can't。嗯。I mean。Is there a maximum stack size for each computer， It's more complicated than that。

 The Sta grows down and at some point it runs out。

![](img/36947c91fbde9e9ddb3e92988d111608_113.png)

![](img/36947c91fbde9e9ddb3e92988d111608_114.png)

Well， okay， so there's a there's actually， I think it's a very interesting question。

 Why do we return。

![](img/36947c91fbde9e9ddb3e92988d111608_116.png)

And peran C instead of C。Okay， so this is address。Oh。Operator。So we are returning the address of C。

 why do we return the address of C because that's that's the heart of our problem， right？



![](img/36947c91fbde9e9ddb3e92988d111608_118.png)

Is that since we're returning the address， we have a problem， okay。



![](img/36947c91fbde9e9ddb3e92988d111608_120.png)

Well， but the。Create cube doesn't return a cube。It returns a。Pointer to a cube。

So if we tried to return C。It would say can't compile。 There is a type error。

 You said you were going to give me a pointer to a cube。And you gave me a cube。

 What do you want me to do with this。 These aren't the same things， right。

 The pointer is where you have stored a cube is the address of a cube， whereas。



![](img/36947c91fbde9e9ddb3e92988d111608_122.png)

![](img/36947c91fbde9e9ddb3e92988d111608_123.png)

The cube would be an actual cube。

![](img/36947c91fbde9e9ddb3e92988d111608_125.png)

This is the custom constructor。 We are giving the parameter to initialize the cube。



![](img/36947c91fbde9e9ddb3e92988d111608_127.png)

To have a width of 20。

![](img/36947c91fbde9e9ddb3e92988d111608_129.png)

Okay， so at this point we crash， so there are a couple of ways we could fix this。



![](img/36947c91fbde9e9ddb3e92988d111608_131.png)

We could change that from not being a pointer and change that， but then create cubes kind of clunky。

 right， It makes a local copy of a cube then copies that in。



![](img/36947c91fbde9e9ddb3e92988d111608_133.png)

Okay。And we kind of want the idea to copy things。

![](img/36947c91fbde9e9ddb3e92988d111608_135.png)

By。To be able to have a function that will allocate new stuff and give it to us， right？



![](img/36947c91fbde9e9ddb3e92988d111608_137.png)

So。So far， we don't really have a way to do that。Because our stack will super great， right。

 because we don't have to work on it。 It takes care of itself， which we love。

As soon as you leave a function， it's gone， right， Things are local to the function。

 And that's why stack variables can be stack。

![](img/36947c91fbde9e9ddb3e92988d111608_139.png)

![](img/36947c91fbde9e9ddb3e92988d111608_140.png)

Variables。can be。He called。Local。Because they are local to the function。

That's to name you here often。

![](img/36947c91fbde9e9ddb3e92988d111608_142.png)

Yes， we're going to do something similar to what you might have seen before and we'll get to that or they can be called automatic。



![](img/36947c91fbde9e9ddb3e92988d111608_144.png)

And they're called automatic because。Autmaticically。Cleaed up。

And those of you coming from Java and had loved garbage collection， right？



![](img/36947c91fbde9e9ddb3e92988d111608_146.png)

This is just like garbage collection， right， It automatically cleans itself up。 when finally。

 we call them stack。

![](img/36947c91fbde9e9ddb3e92988d111608_148.png)

Because on the stack。So we see all these things as as the way we did it。

 garbageb collection was great。 It solved our problems and。



![](img/36947c91fbde9e9ddb3e92988d111608_150.png)

But we don't have that now so what would happen when I run this program？



![](img/36947c91fbde9e9ddb3e92988d111608_152.png)

I don't know we could crash。Because when we do this， it might say you don't own that memory。



![](img/36947c91fbde9e9ddb3e92988d111608_154.png)

We could。Get garbage because we're reading whatever some function left。



![](img/36947c91fbde9e9ddb3e92988d111608_156.png)

O。But how do we deal with wanting to。Actually， return data。Alllocate stuff， and return it。



![](img/36947c91fbde9e9ddb3e92988d111608_158.png)

Well， a number of people have pointed out instead of stack memory， we have heap memory。Starts。

Low in memory。Not quite at the bottom， but it starts down in memory。

 you see I have a low number here instead of that FFF at the start， this is just 4，2，0，0，0。

 so this is a much smaller place in memory。

![](img/36947c91fbde9e9ddb3e92988d111608_160.png)

![](img/36947c91fbde9e9ddb3e92988d111608_161.png)

![](img/36947c91fbde9e9ddb3e92988d111608_162.png)

We'll get to that。And it grows up as things get allocated， they get placed here， and in general。

 they move up。

![](img/36947c91fbde9e9ddb3e92988d111608_164.png)

Grow。Up。From。Start。Okay。So。If we think of all of memory。Somewhere down here， we have the stack。

All right sorry， we have the heap。And it's going this way。Somewhere up here。We have the stack。

And it's going that way。What could happen well。

![](img/36947c91fbde9e9ddb3e92988d111608_166.png)

On a modern machine， this isn't going to happen because of the amount of space of physical memory there is。

 you could just run out of memory， but on older machines。

 there used to be something that happened where， well。

 if my heap got too big and my stack got too big。

![](img/36947c91fbde9e9ddb3e92988d111608_168.png)

![](img/36947c91fbde9e9ddb3e92988d111608_169.png)

![](img/36947c91fbde9e9ddb3e92988d111608_170.png)

We have。A heapt collision。You owe all memory， no matter what you read from zero upwards。



![](img/36947c91fbde9e9ddb3e92988d111608_172.png)

The objects， the things that are allocated on the stack start at the top and are allocated down。



![](img/36947c91fbde9e9ddb3e92988d111608_174.png)

The things on the heap start at the bottom and are allocated up。

 but you always start from the address and read to the higher thing。Okay。

So the difference between the heap is。The heap allows things to stick around。

I read somewhere online that the heap allocates memory randomly。 That's not true。

 There's something called heap space randomization， which is probably what you heard of。

 which is in order to make it harder for someone that is trying to hack your program to do it。

 One of the things that gets done is that。You can。Your heat starts somewhere and because on modern machines we have a lot more memory space than we have physical memory。

 you can move where that place is randomly around to make it harder to guess what's happened。



![](img/36947c91fbde9e9ddb3e92988d111608_176.png)

![](img/36947c91fbde9e9ddb3e92988d111608_177.png)

![](img/36947c91fbde9e9ddb3e92988d111608_178.png)

So。Okay。So how do we get memory on the heap， right， memory on the stack was easy。

 we just wrote variables， it was exactly what we were used to。😡，But how do we get memory on the heap？

Well， I am sure those of you who have already been yammering about it coming from C+ coming from ECE think you know how to get memory on the heap。



![](img/36947c91fbde9e9ddb3e92988d111608_180.png)

![](img/36947c91fbde9e9ddb3e92988d111608_181.png)

There's a word that you guys have thrown around sometimes that we're never going to use。

 It's the bad word。

![](img/36947c91fbde9e9ddb3e92988d111608_183.png)

Now news is a fine word。News R word。Yeah。The bad word。So in the evil sea days as opposed to C+ plus。



![](img/36947c91fbde9e9ddb3e92988d111608_185.png)

Maoc was a thing you used。 We're never going to use malloc here。



![](img/36947c91fbde9e9ddb3e92988d111608_187.png)

We're going to all use。New。So when we in C++。U。Want to。



![](img/36947c91fbde9e9ddb3e92988d111608_189.png)

Alloccate memory。We are going to use the keyword new。



![](img/36947c91fbde9e9ddb3e92988d111608_191.png)

And what does the new do， New says it's how we get memory。



![](img/36947c91fbde9e9ddb3e92988d111608_193.png)

And we do it。 It does three things for us。

![](img/36947c91fbde9e9ddb3e92988d111608_195.png)

So what's the first thing for？Well。There isn't an assignment called Maloc in this class。Memory。嗯。

Ziheap。So the first thing it does is it allocates memory on the heap for us。

And we'll talk about how it works。So if you go new。You have to also tell it。 New what。Why knew what。

 knew what， Because it tells it how much space it needs and knew what。

 Because the second thing it does。 And this is the part that is shared with bad word。



![](img/36947c91fbde9e9ddb3e92988d111608_197.png)

![](img/36947c91fbde9e9ddb3e92988d111608_198.png)

Shared with。We're just going to say C。Shared with the behavior in C。

 It's allocating memory on the heap。 But the second thing it's going to do is going to call。

Constructor。In C plus plus， you don't just ask for memory。 You say。

 please give me the memory to hold。

![](img/36947c91fbde9e9ddb3e92988d111608_200.png)

![](img/36947c91fbde9e9ddb3e92988d111608_201.png)

A cube to hold an integer， to hold a pointer to a cube。And when you do that， if it is a class。

 it will construct it。If it is not a class。It will value constructed， so it'll value initialize it。

 which means it will be when allocated with new， it will be zero or null。😡，Depending on its type。

Okay， and what else it'll do， It'll finally return。The address。Of。Allocated memory。

I'm actually above。Many say allocate memory。Or the address of the object。



![](img/36947c91fbde9e9ddb3e92988d111608_203.png)

A newant will not technically call a constructor because integer as a built in type has no constructor。

😡。

![](img/36947c91fbde9e9ddb3e92988d111608_205.png)

A new int will value initialized memory， so it'll be zero。So from a formal sense。

 it's not a constructor， but we will just in this class not differentiating。

 we will not differentiate between calling a constructor and value initializing。😡。



![](img/36947c91fbde9e9ddb3e92988d111608_207.png)

![](img/36947c91fbde9e9ddb3e92988d111608_208.png)

So whenever you use new you will will talk about it calling the constructor。

 but from a very technical spec way it will be value initializing on primitive memory。

 So these three things are really useful because if we think about this。



![](img/36947c91fbde9e9ddb3e92988d111608_210.png)

![](img/36947c91fbde9e9ddb3e92988d111608_211.png)

![](img/36947c91fbde9e9ddb3e92988d111608_212.png)

In Java。

![](img/36947c91fbde9e9ddb3e92988d111608_214.png)

We have the same sort of structure， right？ We don't want to deal with all the details when we're writing our code。

 So we create objects， get them initialized and。

![](img/36947c91fbde9e9ddb3e92988d111608_216.png)

![](img/36947c91fbde9e9ddb3e92988d111608_217.png)

Get them to us。So is there an advantage of using the word we shall not speak？



![](img/36947c91fbde9e9ddb3e92988d111608_219.png)

Not really。It exists in C++ in the most technical sense。

 but that's because C++ is defined to work as。C also。

 or at least was up until the most recent C standard。It does less work。



![](img/36947c91fbde9e9ddb3e92988d111608_221.png)

Right， it does this thing and it does that thing。

![](img/36947c91fbde9e9ddb3e92988d111608_223.png)

But it doesn't do this middle part。

![](img/36947c91fbde9e9ddb3e92988d111608_225.png)

We are always going to want to do this middle part because we always want our variables to be objects or。

😡。

![](img/36947c91fbde9e9ddb3e92988d111608_227.png)

Elements， right， we want them to be initialized。 We want them to be things we work on。

 We don't want them just to be raw memory。

![](img/36947c91fbde9e9ddb3e92988d111608_229.png)

![](img/36947c91fbde9e9ddb3e92988d111608_230.png)

In a sense。Computer science has come forward and this is something that we now recognize。



![](img/36947c91fbde9e9ddb3e92988d111608_232.png)

Okay， so this gets us。

![](img/36947c91fbde9e9ddb3e92988d111608_234.png)

Yes， so that's actually a very good question。 So three means new returns a pointer。 Absutely right。

 The return value of new is going to be a pointer to memory， not。



![](img/36947c91fbde9e9ddb3e92988d111608_236.png)

The memory itself。New returns a address， so you're going to need to store the value returned by new in a pointer to the correct type。



![](img/36947c91fbde9e9ddb3e92988d111608_238.png)

![](img/36947c91fbde9e9ddb3e92988d111608_239.png)

For example， what you would want to do is something like cube。Star。C equals new。Cubbe。

20 and that would。Iitize C to point at a cube instantiated by calling the custom constructor with an argument of 20。



![](img/36947c91fbde9e9ddb3e92988d111608_241.png)

![](img/36947c91fbde9e9ddb3e92988d111608_242.png)

Does it have to be a pointer？To store an address， yes。The where we put addresses is pointers。

That's where we put them。

![](img/36947c91fbde9e9ddb3e92988d111608_244.png)

Otherwise， it'll be a type error。In fact， it will be a pointer to the type that it created。



![](img/36947c91fbde9e9ddb3e92988d111608_246.png)

![](img/36947c91fbde9e9ddb3e92988d111608_247.png)

The variable， which variable this variable C is whatever scope that it was created in this new。



![](img/36947c91fbde9e9ddb3e92988d111608_249.png)

Lasts until you take care of it。 So what we had called stack memory。



![](img/36947c91fbde9e9ddb3e92988d111608_251.png)

嗯。Automatic。Heap memory is not。

![](img/36947c91fbde9e9ddb3e92988d111608_253.png)

Heap memory is not。 Heap memory we are required to take care of。



![](img/36947c91fbde9e9ddb3e92988d111608_255.png)

![](img/36947c91fbde9e9ddb3e92988d111608_256.png)

You're asking， can I use star C globally， where did I declare star C？



![](img/36947c91fbde9e9ddb3e92988d111608_258.png)

Star C is a variable。 This is created somewhere。 I can use it in wherever it was created。



![](img/36947c91fbde9e9ddb3e92988d111608_260.png)

So in general， we only use new if we're creating a pointer。

 we only use new when we want to allocate memory on the heap。

 we want to allocate memory somewhere other than the stack。

 and it turns out there's a couple of reasons you might want to do this。😡。



![](img/36947c91fbde9e9ddb3e92988d111608_262.png)

![](img/36947c91fbde9e9ddb3e92988d111608_263.png)

![](img/36947c91fbde9e9ddb3e92988d111608_264.png)

![](img/36947c91fbde9e9ddb3e92988d111608_265.png)

嗯。That one， your stack actually is limited to being of some size。



![](img/36947c91fbde9e9ddb3e92988d111608_267.png)

This is the type。Of。Xi。So C is a pointer to a cube。Star C would be dereferencing the pointer。Okay。So。

 okay。So we want to do this。Sometimes。

![](img/36947c91fbde9e9ddb3e92988d111608_269.png)

We want to do it when we need to allocate something very large because there's probably not enough space in the stack to do it。



![](img/36947c91fbde9e9ddb3e92988d111608_271.png)

And we want to do it when we want it to live outside of returning from the function that we allocated。

But there's a downside。 Nobody takes care of this memory for us。



![](img/36947c91fbde9e9ddb3e92988d111608_273.png)

So how do we take care of this memory？

![](img/36947c91fbde9e9ddb3e92988d111608_275.png)

Well。There's a word that is wonderful， but。Yin。C is used for this and we don't do that。Yeah。

So we don't allow free， yeah。Right， so free。Is a bad word here。But we use delete。

What does deletelete do？Delete is how we tell the system we are done with。嗯。



![](img/36947c91fbde9e9ddb3e92988d111608_277.png)

Memory。We say we don't need this anymore， right when we return from a function。

 the stack cleaned up when we。

![](img/36947c91fbde9e9ddb3e92988d111608_279.png)

What are done with memory that we've allocated with new， we are going to use deletete。



![](img/36947c91fbde9e9ddb3e92988d111608_281.png)

![](img/36947c91fbde9e9ddb3e92988d111608_282.png)

And that's the only way we get it away with it。That's the only way we free it up。And what does it do？

It does two things。Yit。Invokes。The deor。

![](img/36947c91fbde9e9ddb3e92988d111608_284.png)

And we haven't talked about destructor much。

![](img/36947c91fbde9e9ddb3e92988d111608_286.png)

But what does a de do， A deor has the job of cleaning up my class。



![](img/36947c91fbde9e9ddb3e92988d111608_288.png)

And right now we've just seen classes that have memory。



![](img/36947c91fbde9e9ddb3e92988d111608_290.png)

But you will find out that in C++， you can have a class and you've seen it， right， that represents。



![](img/36947c91fbde9e9ddb3e92988d111608_292.png)

A file。

![](img/36947c91fbde9e9ddb3e92988d111608_294.png)

So when I'm done with that class， I want to do things like close the file。



![](img/36947c91fbde9e9ddb3e92988d111608_296.png)

So。Cleans up。Po。

![](img/36947c91fbde9e9ddb3e92988d111608_298.png)

And for the people that were asking the difference between new and C++ and new and Java。

 just don't even think about Java， there's a similarity。

 just think about C++ as a different language。

![](img/36947c91fbde9e9ddb3e92988d111608_300.png)

That。

![](img/36947c91fbde9e9ddb3e92988d111608_302.png)

So it cleans up the class。Right， if I had a class that represented an FTP connection。



![](img/36947c91fbde9e9ddb3e92988d111608_304.png)

That the FTP deor would do things like close the connection to the FTP server。 It would。



![](img/36947c91fbde9e9ddb3e92988d111608_306.png)

Clean up， and we will be doing this， because we'll find as we start writing classes that represent complicated data structures that they have pieces that need to be cleaned up。

 And the deor is a tremendously helpful tool to do that for us。 And then what does it do。

 it then deallos。

![](img/36947c91fbde9e9ddb3e92988d111608_308.png)

![](img/36947c91fbde9e9ddb3e92988d111608_309.png)

![](img/36947c91fbde9e9ddb3e92988d111608_310.png)

The memory。So it can be reused again。

![](img/36947c91fbde9e9ddb3e92988d111608_312.png)

And this， this part 3 is super important。The thing that is hard。嗯。

About C plus plus is this is managing memory and making sure we don't forget about it。

 that we clean it up when we're done and that we allocate it when we need it and that we are consistent。



![](img/36947c91fbde9e9ddb3e92988d111608_314.png)

So is the deor something native to the language or is it something that we create ourselves both？



![](img/36947c91fbde9e9ddb3e92988d111608_316.png)

![](img/36947c91fbde9e9ddb3e92988d111608_317.png)

That all classes。Have a deor。Much like we start out with。Having a constructor， right， the default。

 if you write nothing， you have the default constructor。



![](img/36947c91fbde9e9ddb3e92988d111608_319.png)

。

![](img/36947c91fbde9e9ddb3e92988d111608_321.png)

Custom Conor will then do the work you want。Well。Imagine。If I create a， well。

 let's think about using。Chrome that I use Chrome as a browser， and I have lots of pages open， right？



![](img/36947c91fbde9e9ddb3e92988d111608_323.png)

Now imagine when I close one of those pages。That page had something in it like maybe it was Netflix because I was watching a show。



![](img/36947c91fbde9e9ddb3e92988d111608_325.png)

When I close it。That memory。Needs to get released because I don't need it anymore， right。

 I'm not watching that video anymore。 That was a huge amount of memory。When I close it。

 I want that memory to be reusable。

![](img/36947c91fbde9e9ddb3e92988d111608_327.png)

Well， in Java， if nothing referred to an object。

![](img/36947c91fbde9e9ddb3e92988d111608_329.png)

It got cleaned up by the garbage collector， right， and that's really nice。



![](img/36947c91fbde9e9ddb3e92988d111608_331.png)

In C plus plus， that's not the case。 If nothing refers to something。



![](img/36947c91fbde9e9ddb3e92988d111608_333.png)

It's still there until you tell the system to get rid of it。



![](img/36947c91fbde9e9ddb3e92988d111608_335.png)

So。Since I don't close my Chrome browser， if every time I closed a page。

 it didn't free up that memory soon， even more soon than already happens， I would run out of memory。



![](img/36947c91fbde9e9ddb3e92988d111608_337.png)

![](img/36947c91fbde9e9ddb3e92988d111608_338.png)

Now， when I close the whole program， the memory will be released。

But what we're writing in this class are data structures。

 things that are containers that will be used by other people， by other programs， right。

 and we have to make sure that our usage of memory for them is correct。



![](img/36947c91fbde9e9ddb3e92988d111608_340.png)

![](img/36947c91fbde9e9ddb3e92988d111608_341.png)

So。

![](img/36947c91fbde9e9ddb3e92988d111608_343.png)

Our way of testing， if you are doing a good job of this is to verify that you free it up。



![](img/36947c91fbde9e9ddb3e92988d111608_345.png)

Um， just like deleting， no， no， deleting actually cleans it well。



![](img/36947c91fbde9e9ddb3e92988d111608_347.png)

The actual implementation of delete from the point of view of what's going on in physical memory is going to be similar to a hard drive。



![](img/36947c91fbde9e9ddb3e92988d111608_349.png)

![](img/36947c91fbde9e9ddb3e92988d111608_350.png)

This is saying that if we do not call delete， nothing deletes things for us， it's not automatic。😡。



![](img/36947c91fbde9e9ddb3e92988d111608_352.png)

That we， if we ask for memory when we're done with it， we have to have a delete。So， every。Newu。Must。

Be matched。With。Hey， delete。Everything you created。Must be matched with something that deletes it。

When you delete it， it's gone。Is there an advantage to having do it to do it manually。

 why not do it automatically Okay， the advantage is possible performance and more precise control。



![](img/36947c91fbde9e9ddb3e92988d111608_354.png)

![](img/36947c91fbde9e9ddb3e92988d111608_355.png)

Also， there was an earlier question about smart pointers。

 so C++ has a feature we're not going to use in this class。



![](img/36947c91fbde9e9ddb3e92988d111608_357.png)

![](img/36947c91fbde9e9ddb3e92988d111608_358.png)

Smart pointers。嗯。Are pointers that can do stuff automatically。But they don't do everything。And。

 in fact， they don't solve all。嗯。

![](img/36947c91fbde9e9ddb3e92988d111608_360.png)

All things in memory。So unique pointers are one of many types of smart pointers。

 and we will not be using it。

![](img/36947c91fbde9e9ddb3e92988d111608_362.png)

Yeah， so。Again。The question here becomes， what kind of work are you doing and when is it better to take care of memory manually versus automatically。

It's a trade off。 It is taking on work to be able to have more control。 Remember。

 C plus plus is a chainsaw language。It can do very peripheralful things。

But it can do horrible things as well。And you're taking on the choice to。嗯。CanHave more control。

 So when it is not freed， why is it lost， Well， if I do not free the memory。



![](img/36947c91fbde9e9ddb3e92988d111608_364.png)

And I no longer know where it is。So if I don't free the memory and I throw out the pointer。



![](img/36947c91fbde9e9ddb3e92988d111608_366.png)

Who has access to it？How can I use that memory？The system still thinks it exists。You haven't told it。

 It's done。But。You don't know where it is anymore。I just let the pointer leave， right。

 if I have a pointer in my function。

![](img/36947c91fbde9e9ddb3e92988d111608_368.png)

My function contains a pointer。 When I return from that function， that pointer gets cleaned up。

 right。

![](img/36947c91fbde9e9ddb3e92988d111608_370.png)

I change the pointer's value to  point。2 elsewhere。



![](img/36947c91fbde9e9ddb3e92988d111608_372.png)

Because when I called new， the operating system said this memory is reserved for you。

 And until tell you， you tell me， I've， I've got a box on my shelf。 And I've said。

 that's Professor Evans's box。 K gets to use that。 No one else does。



![](img/36947c91fbde9e9ddb3e92988d111608_374.png)

![](img/36947c91fbde9e9ddb3e92988d111608_375.png)

![](img/36947c91fbde9e9ddb3e92988d111608_376.png)

If I forget that I have that box。Then I don't。I don't know， but that box is still on the shelf。

 and no one else can have it because the system knows。Carl owns that box。 So if he asks for it。

 I'll give it to him。 If anybody else says， hey， can I see what's in that box， no。You can't。😡。

It's still there。It's still taking up space on the shelf。No one can have it。If I keep doing this。



![](img/36947c91fbde9e9ddb3e92988d111608_378.png)

I could just start trying to read random locations in my computer。 And if， if I just say， hey。

 I'm going to look in that box。 If I happen to own it， that's okay。 If I don't own it。

 the system says no， you can't look in that box and and kicks me out。



![](img/36947c91fbde9e9ddb3e92988d111608_380.png)

If I get deleted， well。

![](img/36947c91fbde9e9ddb3e92988d111608_382.png)

Nobody knows what's in that box Now， it turns out that when my program exits， that gets cleaned up。



![](img/36947c91fbde9e9ddb3e92988d111608_384.png)

But we have programs that run on for a very， very long time。



![](img/36947c91fbde9e9ddb3e92988d111608_386.png)

![](img/36947c91fbde9e9ddb3e92988d111608_387.png)

Okay。So what's the difference？So we have two kinds of memory。

 and this is really all we're going to talk about in this class。

 There technically is one more kind of memory， which is global memory。

 but we're never going to talk about global memory in this class。

 We have heap memory and stack memory。

![](img/36947c91fbde9e9ddb3e92988d111608_389.png)

![](img/36947c91fbde9e9ddb3e92988d111608_390.png)

So what do we have， we have the stack。Grows down。It's automatic。And allocated。When functions。

Functions。Start。Released。When。They end。That's the stack， it's great， it's very efficient。

 it's very simple， but you could only have so much of it。And。You can't keep it outside of a function。

We have the heap。Managed。By programmer。The programmer is responsible for it。Growve。Up。And。Allocated。

Explicitly。By new。Dal located。Explicitly。By delete。That's it。

These are the two places we're going to put things in our program。



![](img/36947c91fbde9e9ddb3e92988d111608_392.png)

We like to use the stack where we can。But if I'm allocating something that's going to exist beyond my function。

 the stack isn't going to do it。Right？I'm going to have to use the heap。



![](img/36947c91fbde9e9ddb3e92988d111608_394.png)

And once I've used the heap， I've taken on the burden of being responsible somehow for that memory。



![](img/36947c91fbde9e9ddb3e92988d111608_396.png)

Well。Is there a reason why the stack grows down and the heap grows up on the same place。

 Why not create two separate places？ Well， in a sense。

 there are two separate places or as much as we can talk about two separate places on a computer。



![](img/36947c91fbde9e9ddb3e92988d111608_398.png)

In your computer， all of the memory in your computer is organized as one big number line。

 It starts at the smallest possible address and goes up to the largest possible address。

 and that's all of the memory that exists in your computer。😡。



![](img/36947c91fbde9e9ddb3e92988d111608_400.png)

![](img/36947c91fbde9e9ddb3e92988d111608_401.png)

![](img/36947c91fbde9e9ddb3e92988d111608_402.png)

So there isn't any other place to put things right， so they chose to have the stack。

 start at the top and grow down and the heap start at the bottom and grow up to keep them as far apart as they could。



![](img/36947c91fbde9e9ddb3e92988d111608_404.png)

![](img/36947c91fbde9e9ddb3e92988d111608_405.png)

Global variables exist for the lifetime of the program。



![](img/36947c91fbde9e9ddb3e92988d111608_407.png)

They are outside the scope of the program in a sense and that's why we call them global。



![](img/36947c91fbde9e9ddb3e92988d111608_409.png)

Are we going to talk about how to pass by reference， yes。

 we are going to talk about function passing and all of that later。



![](img/36947c91fbde9e9ddb3e92988d111608_411.png)

Is he memory somehow faster than the stack？No。

![](img/36947c91fbde9e9ddb3e92988d111608_413.png)

In fact， in general， the stack is faster that said。

 the stack will end up with copying in a more frequent case。



![](img/36947c91fbde9e9ddb3e92988d111608_415.png)

Well。

![](img/36947c91fbde9e9ddb3e92988d111608_417.png)

2 to the 64th。Is a very big number and you really don't have to worry about running into each other。



![](img/36947c91fbde9e9ddb3e92988d111608_419.png)

The heap， sorry， this stack has a more limited maximum size and it's not really because it's going to run into the heap。

 but it turns out when you get to learning in more details about operating systems either in ECE391 or CS241。

 you'll find out that there are other things that go in memory。



![](img/36947c91fbde9e9ddb3e92988d111608_421.png)

![](img/36947c91fbde9e9ddb3e92988d111608_422.png)

![](img/36947c91fbde9e9ddb3e92988d111608_423.png)

And some of those go actually in between the heap and the stack at this point。



![](img/36947c91fbde9e9ddb3e92988d111608_425.png)

So。Okay。So let's walk through a simple bit of code here。So now I have a more complicated program。

 and I think in the time I've got， we can walk through all the pieces of it。 So the first line。

 the first thing I'm going to do is right here， I have my heap。Or sorry， here I have my stack。

And here I have my heap。Yes。Two to the 64th is 64 bit addressability。So。U。

I don't know how long that's been there。Oh。

![](img/36947c91fbde9e9ddb3e92988d111608_427.png)

Okay， so the first thing I'm going to do is I'm going to create a。



![](img/36947c91fbde9e9ddb3e92988d111608_429.png)

Thing called C1， which is going to be a cube pointer。Called C1。

And it's going to be on the stack and it's going to be there。And then I'm going to call new。

And so down here， I'm going to create a cube。And a cube， it turns out， is going to。Take8 bites。

Because the only thing in the cube is a double， it's going to fit there。

 And if you remember when we chose， we chose that our default constructor would set it to one。

 so it's going to be 1。0。

![](img/36947c91fbde9e9ddb3e92988d111608_431.png)

And I could write the numbers here， but I'm going to draw a pointer instead。



![](img/36947c91fbde9e9ddb3e92988d111608_433.png)

So this is going to now be pointing。There。Okay。Now I'm going to create cubebe C2。

This is going to be a cube pointer C2。And you will note there is no name here。This is a cube。

But it does not have a name。Okay， what is cubeB C2 going to do？

Cubbe C2 is a pointer and it's going to be initialized to C1。So it's going to point there。Okay。

So they point to the same thing， then we're going to do set length。

 so we're going to change this length Q 10。Isn't that a pointer to a pointer， no？C 1 is a pointer。

 It contains an address。 What did we do， We initialized C2， which is a pointer。



![](img/36947c91fbde9e9ddb3e92988d111608_435.png)

And we copyied that value， if we want me to write the value， I'd have 42000。



![](img/36947c91fbde9e9ddb3e92988d111608_437.png)

0。4，2，0，0，0， right？Not a problem。Um， iss cubebe C2？Is C2 the line cubed star C2 equals star C1， No。

 that would be a type error that would be trying to put the value of C1 in C2。



![](img/36947c91fbde9e9ddb3e92988d111608_439.png)

If I did cube pointer pointer C1 equals address of C sorry C2 equals address of1， that would be fine。



![](img/36947c91fbde9e9ddb3e92988d111608_441.png)

No， C2。Is cop， right。Put。Contents。Of C 1 in C2。

![](img/36947c91fbde9e9ddb3e92988d111608_443.png)

Okay。And then we set the value， and then we delete C2， so we release this memory。



![](img/36947c91fbde9e9ddb3e92988d111608_445.png)

And then we delete C1。Oops。Sosu。We then look at C1。And here we're going to crash。



![](img/36947c91fbde9e9ddb3e92988d111608_447.png)

Yeah， so if we made star C2 equals address of C1， it would try to point to C1 and we would get a type error。

 but yeah， C1 is already deleted。 so at this point we crash。



![](img/36947c91fbde9e9ddb3e92988d111608_449.png)

![](img/36947c91fbde9e9ddb3e92988d111608_450.png)

And we crash。Because we've already freed up that memory。



![](img/36947c91fbde9e9ddb3e92988d111608_452.png)

Well， we're not deleting the pointer， delete deletes what that pointer points to。😡。



![](img/36947c91fbde9e9ddb3e92988d111608_454.png)

When C1， when we exit Maine， C1 goes away， it's fine。RightDe deletes this thing。



![](img/36947c91fbde9e9ddb3e92988d111608_456.png)

Delete， delete whats what it points to C1 and C2 or on the stack。



![](img/36947c91fbde9e9ddb3e92988d111608_458.png)

The cube created by new is on the heat。We could change the length either way with C1 or C2。

 They are two now pointers pointing at exactly the same。And that's what I've got for today。

 I'll stick around and answer questions， but that's the end of what I am doing that is new material。



![](img/36947c91fbde9e9ddb3e92988d111608_460.png)
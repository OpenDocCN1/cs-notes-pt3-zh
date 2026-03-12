# 中英-•-C++和C语言ACCU大会2024｜人工智能｜架构｜函数编程｜静态分析｜安全｜编译器｜开发者｜垃圾回收｜链接器｜代码生成｜cmake-p22-P24-An-(In-)Complete-Guide-to-C++-Object-Lifetimes---Jonathan-Müller--BV1pNotYYELk_p22-

![](img/56fba6d34face213c80b8ac2ab581eec_0.png)

So this is my talk。 I originally titled it a complete guide to C++ objectject Lifes。

 But then I figured Id better have the insurance in there。 because it's a lot of material in there。

 And there's a lot more。 I could talk about if I had even more time。 But don't worry。

 the talk is gonna be organized in levels。 So we're gonna start with the very basic。

 And then we go deeper and deeper until we reach the area of open standardization research problems in order to fix fundamental bugs in the specification。

 So you can stop watching the YouTube video at any time and you won't miss anything out。😊。



![](img/56fba6d34face213c80b8ac2ab581eec_2.png)

So。After the end of each level， if you like you can ask questions pretending like if there are critical questions。

 feel free to ask them in between the talk。 if there are more in-depth discussion。

 we can do that at the end。 And also in the early parts。

 lots of questions are probably gonna be deferred to the later levels。

 But if you're sitting on the very right， I can't see you if youre at the in the back。

 if you have questions I can't see your hand because of the lights So just show or something。

 So let's begin。 So I'm gonna talk about object lifetimes。

 which means the first question is what are objects and what lifetime。😊。

And objects in here in this context have nothing to do for object oriented programming。

 Objects are fundamental to C plus。 It's a terminology of the C plus test standard uses。

 And essentially everything you do in C plus tests。Does something with objects。

 so this is a quote from the standard。 We're gonna see those a lot。

 The constructs in a C plus+ program create， destroy， refer to access and manipulate objects。

 So all the C plus+ program does is manipulate objects。 And to understand objects。

 we need to understand three terms storage。😊，belium。And type。So let's begin with Stch。so。

The C++ program has memory， which consists of bitetes。It's a sequence of contiguous bites。

 and every byte has a unique address。So here's a bit of memory。 Like， it's just a bunch of bytes。

 and these bys store bits， and the bits have some numbers I've given in there。 And for example。

 we've got the highlighted by， which has the value of 41。😊，Now。

 Oaks 41 is just a big pattern in the byte。 But what does it mean， right？ What does Oaks 41 mean。

It could be the8 bit integer 65。It could be the SK character， capital A。

It could be the start of the string that begins with capital A or somewhere in the middle of a string that has a capital A。

 It could be part of a 32 B integer。 So together with 3 mo， it makes up a 32 B integer。😊。

Or it could be anything else， like it could be some inum value。 it could be part of a flow， whatever。

And this is the distinction between the physical bits and the value。

So the sort of the Bible of C plus U elements of programming gives a good definition of value。

 So we've got a datum， which is just a sequence of0 and 1。 And this datum can be our awake 41。😊。

But on its own， its meaningness， only together with some interpretation does it become a value。

So a value is an interpretation of a sequence of bits to represents a mathematical thing。

 Like a value is a mathematical term。 It's a mathematical。 It's unchanging。 It lives forever。

 It's a mathematical idea。 It's the number 42。And then the dat is like a physical representation of that thing in memory。

And now a type simply specifies the interpretation of a datum。

 So it's essentially a function from datums to their values。So， for example， we have to type on。

 and it means that you take1 bite of memory。 that's aud datum and to interpret it as an8 bit un site integer to get the value。

Or we can have the type in， there we take 4 B of physical memory and interpret the bits as a tooth complement 32 B integer。

We can have more complex types like stood string。 So then we take 24 by。

 The first 8 B are pointer to nu termmininated string。 Then we've got size and the capacity。

 And so we take the physical bits and interpret it according to the walls of a type。

 And then we get a mathematical value。😊，And now an object。Has a particular type。

 occupies a region of storage， and at a particular address， where it stores the volume。

So there's an object。 It has a type。 It lives somewhere in memory， where it stores its value。

So here we've got some code。 we first create an in object。 We call it x。

 and we give it the value of 42。 And then we've got the second object， a float object。

 we give it the value of 3。14。 And now we've got two objects。 They live some very memory。

 They store some value。😊，And the value of an object can change over time。 So， for example。

 we can assign the x a new value and now x stores the value 11。Unless the object is constant。

 then the value can't change。 But in principle， an object has a value at a given point in time。

 and this could change over time。And like in contrast， the value is just a mathematical thing。

 A value never changes。 Like the number 42 is always gonna be 42。

 It doesn't suddenly change later on。 Only an int object can have the value 42 and later on change that。

Now， it's important to point out at this point that functions， for example， aren't objects。

 Functions are their own thing。 Even though they can have an address， they're not really objects。

 only function point as object。 So here we have a function F。 This is not an object。

 This is a function。 And then we've got a pointer to F。 This is an object。

 and that value is the address of F。So the object is the thing that can change。

 that can be a that can be manipulated， and the function is just some piece of good。And similarly。

 references aren't objects。 Refferences are simply aliases to existing objects。

 So here we having just one into object X。 And then we've got two names for that。

 The variable X itself， and then an alias ref。 So references on its own aren't theyre just simply aliases。

 They don't have properties on their own。 They just have the properties of the object they were reference to。

Now， what is lifetime？The lifetime of an object is a one time property of the object。

So an object has a type， an object has an address。 An object has a value。

 and an object also has a lifetime。 just another property。 It's a pretty important property。

Because all the other properties of an object。Only applied during its lifetime。

If you access an object that is outside its lifetime， it's not alive。 you can't do anything。

 You can't do a lot with it。Like， there are significant restrictions on the use of an object before the lifetime has started and after the lifetime has ended。

 So it's important to understand when objects are alive in order to write concrete code。

So this is a very high level picture。The object lifetime in a nutshell。 The first step is always。

 we allocate storage for object。We then initialize an object which starts the lifetime。

So 맨 then 없 yeah。So the initialized is in question marks because you don't really need to initialize an object in order to start it。

 but we'll cover the details later。But once we have the lifetime we can use the object。

 We can change its value， We can read its value。 We can do stuff with it。Then at some point。

 we're going to destroy the object， which ends the lifetime。And at some point， hopefully， after that。

 you're gonna delocate the storage of the object。And this is the high level picture。

 And the rest of the talk just kind of looks at the details。So important note about terminology。

The Splpha standard describes that objects can be created。And when an object is created。

 it just means that we've got the mathematical thing， some object， which has some properties。

 which we can start to talk about。 but it does not necessarily start lifetime yet。

 It just means that we know got the thing an object。 we can talk about it。 And at some later point。

 we're gonna start that lifetime。However， on the flip side， when an object is destroyed。

 This is actually a physical operation we can do on the object， which ends the lifetime。

So there's a bit of an asymmetry in the terminology here。

 So create just means we have something we can talk about and then destroyed actually means we end the lifetime。

 So destroyed is a onetime operation that we actually do。

I'm gonna try to avoid using cr to mean start the lifetime。 but like it's the croal usage。

 So I might slip up there。 But like technically， it's like a different thing。

 like we create an object， which just means it's something we can now start talking about it。

 And then we we can， for example， start the lifetime market。

And also note that lifetime is something the standard invented in order to describe the semantics on C plus plus program in the specification。

 It has absolutely nothing to do with the actual physical machine where program runsson。

 like objects arent CPU thing。 objectsject are C plus plus standard thing。😊。

And all the standard talks about for lifetime is just in order to describe Ben the program as valid when a program is invalid and so on。

 So this is very abstract theoretical talk。 And we're gonna encounter some things which are undefined behavior。

 but just because the specification is a bit buggy and， which aren't really any problems in practice。

So with that， let's begin。So level0 variable declaration。

We're going to see inted objects slash paragraph1 a lot。

 and which is a sentence that' describe when objects are created。

 and one of those places is using a definition。😊，So， for example， in this code。

 we have an invariable definition which creates an objects。

 also allocates storage for and starts its lifetime。We can then use the object， read it， modify it。

 read it again。 And then in the end， it's destroyed。And to understand the details about when exactly。

 we allocate the storage for that object。 And when we start the lifetime。

 we have to look at the storage duration of the definition。😊。

So the storage duration is another property of an object。

 and it defines the minimum potential lifetime of the storage containing the object。

And it's determined by the construct we use to create that object。

 So depending on how we got the object， we have different storage。And here in this particular case。

 we are only dealing with static fit and automatic storage duration。

 which is the storage duration of awareness。Automatic storage St is the easiest one。

When we've got a variable that's inside the block or em metscope and doesn't use any special keyboards。

 It has automatic storage duration。 It's created。 The storage is allocated when we enter the when we and encounter the definition。

 And when the block exits， we are gonna display it。😊。

So when we start executing a main function and we reach the first line， we allocate towards5。

We then allocate storage for B。 We then enter a nested block。 So allocate storage for C。

 Then we exit the block， which delocate storage for C。

 And then we delocate A and B when we exit the function。 This is automatic storage。 This is。😊。

Very straightforward。St exation variables at like names risk global variables。

And their stored is allocated when the program starts and delocated when the program ends。So here。

 we've got a bunch of global variables。 They all have static storage duration。

 And when the program starts up， we allocate storage for them。 And when the program terminates。

 we allocate storage for them。 So throughout the entire lifetime of the program。

 we've got storage for those。😊，Fat storage duration is similar。

 many variables detect that per threat local。 but instead of having once one object throughout the entire program。

 we having one per third。 And when the threat starts， we allocate the storage。

So here when we start executing main， we having one copy of the threat local variable whose lifetime is going to match the whose storage duration matches the storage duration of the main threat。

😊，And when we execute started the second thread， we will allocate a second copy of that。

 And this lifetime will then only last as long as the the storage duration only last for the second we。

 So when we destroy the second thread， we also delocate the thread local variable for that thread。

 And when we exit the main thread， we delocate the threat local storage for the other way。😊，Now。

 in general。The store situation is not the same as the lifetime of an object。

Just because we've got storage for an object doesn't mean the lifetime started yet。

The lifetime only starts when。We've got storage and we completed the initialization。

So when are the variables initialized， but for automatic start duration？😊。

When the storage is are located。 So in this case， storage duration and lifetime executive matches。

 So when we allocate storage， when we enter encounter the definition。

 we also start the lifetime of the object。However， for static and F storage situation is complicated because global variable initialization depends on a lot of factors。

 We've got function local statics， which are initialized at different point and global objects outside of a function。

 we've got constant and dynamic initialization and nifty counters and the module dependency graph and inline variables。

 I gave an entirely separate talk just about when the global variables are gonna be initial。😊。

Because even though the storage exists the entire time。

 the initialization happens potentially happens at a different time。

 And only then does the lifetime start。 So there's entirely a different talk you can watch after the moment if you're interested。

😊，But for automatic storage， when we've got storage， we've got be the lifetime。

 and we can start using the object。Now， the initialization is entirely optional because in general。

 we can start an object。Start the lifetime of it without a known value。

So more precise when we allocate storage for an object。And we don't initialize it。

Then it has an indeterminate value。And it will keep having an indetermined value until we give it a different bond。

 And when we read something with an indetermined value， we have undefined behavior。So for example。

 when I' just right in the x， this allocates storage， but that doesn't do any initialization。😊。

Because the default constructor does nothing。So， but it nevertheless starts a lifetime because we done any initialization we wanted to do at this point。

 which is just， we didn't want to do any initialization。 So the lifetime starts。

 and we have an innument value。This means it's undefined area to read the variable because it doesn't have a noun value。

But it's not undefined behavior， behavior to assign something to it。 because we。

 even though we didn't do any initialization， we've got an object。 This lifetime started。

 We can start using it。 We just can't read it yet。And then the second read is okay。

And now the current quote says the behavior is undefined when we read in value of undetermined value。

 This actually kind of change in C plus plus 26。So in C plus 26。

 we're going introduce erroneous behavior。 and erroneous behavior is essentially what undefined behavior should have been in many cases。

 So with undefined behavior， the compiler can assume that it doesn't happen and optimize accordingly。

 If erroneous behavior， the compiler can do that。 But the compiler is allowed to do is to issue a diagnostic and terminate the program。

 So sort of a contained version of undefined behavior。And in C 26。

 read of an indetermined value is erroneous， not undefined。

 So the compiler is allowed to catch it dynamically at onetime when it attends。

 but is not allowed to optimize based on the existence of wes。

 So we're gonna limit undefined behavior in that area in C 26。That is level you。

 Any questions so far about object lifetime。 Yes， at the very quick。So what's the cost。

 I'm not prepared to answer that at this time。But， yes， it's a trade off。 They're。

 They're gonna look at that。Various cases on a case by case basis， but yes。Okay。

So let's move on to level 1， new and delete。An object is also created by a new expression。

So when we have a new expression， we create an object。Then we also need to destroy it。

 using a delete expression。But this is pretty straightforward。 So when we write new ins。

 we create an object。 We allocate storage for it。 We start this lifetime。😊。

We can then use that object freely。😊，And then we delete it。 We destroy the object。

 derocate the storage and end the lifetime and derocate the storage。This put is straightforward。

And just like with regular variables， it's also possible to create one with indetermined values。

 right new ins without anything starts to laughing。 Actually， I think that's not true。I think。Now。

 I think， yeah， it's an indeterminate video。 So we can have。The undefined behavior， when we read it。

 but when we assign it， it's okay。And that's level one。

It's even easier because we have full control over when the object is allocated。

 when the lifetime starts and when it's ded。So let's start about something more interesting。

 temporary objects。An object is created when a temporary object is created， which is a great toology。

So consider this code。 We've got a function F， which takes a reference to an in constant。

 and then we're calling it with the number 42。Now， the number 42 is a PR value。 right。

 It doesn't live anywhere in memory。 It's the number 42。 We can it doesn't have an address。

 We can't modify it because it's always going to be 42。But what does the reference by。

 Like a reference is an alias font object。 So thats the object came from。

 And the answer is to compiler has to create a temporary object， Give it the value 42。

 and then have the reference be an alias for that， because the reference can't bind directly to a value。

 A reference is an alias font object。 And it needs an object in order for a reference to make sense。

The technical term for this is temporary materialization conversion。

 which is a great phrase for Hgman。And the description reads like somebody was desperately trying to hit a word count。

So when we've got a P R value of type T， which is this number 42， for example。

 it can be converted to an x value of type 2， which is just an R value reference to T。

This conversion initializes a temporary object of type T from the PR value by evaluating the PR value with the temporary object as the result object and produces an x value denoting the temporary object。

Make sense， but but what it essentially says， we've got a PR value。 We need an object。

So we will create an object， give it the value of the PR value， and use it。😊。

And this happens every time where we use a PR value， but you actually wanted an X value。 For example。

 we want to bind a reference to PR value。 like in our previous case。

 this has to be an R value reference or a constant L value reference because a noncon L value reference doesn't bind to a number 42。

 You can't have an in equals 11 on。Most compilers。Alsos if you want to do member access on a PR value。

So you've got a function that returns the stood string by value。 This is a PR value。

 And then you want to call dot size。 dot size gets there this pointer。

 So we need an address of something。 So we need to create a temporary object。

 initialize it from the PR value in order to use it。😊，Also， when we use As。

 because Airs really want to repoint us。 So whenever we use an A， we will create a temporary object。

😊，And interestingly， when we discard the results of a function that returns a PR volume。

 So a function that returns a stood string by PR value。 This is just a value。😊。

But we want to run the deor when we destroy it。 But in order to run the destruct。

 we first need to create an object in order to run the destruct。

 So when we just call a function that returns a PR value and ignore the result。

 we will create a temporary。Now， what about the lifetime of this temporary。Creation is easy。

 And if we create the temporary， the lifetime starts immediately。

And the temper is then destroyed at the last step of the full expression that contains it。So here。

 we've got a function F， which takes a bunch of references to create false creation of temporaries。

 And then we call it with 11 and to PR value with turn from G。

 This creates two temporary objects whose lifetime starts immediately。😊。

Then we evaluate the quality of the function F。 And once we're done in control for we just the semicolon。

 we destroy those temporaries。And this means that by we are inside F， we can free use the reference。

 right because the reference will point to the temporaries that will outli the quality of the function。

Why we are inside F。If you take the adver of those and store them somewhere else and use them later on the existing memory that has been destroyed right because they destroy them after the call。

 also， when we return a reference to them。This can be a problem。Now。

 there are two exceptions to addresspo。This is called temporary lifetime extension。

The first one happens when we have a reference that is bound to temporary directly。

 the lifetime of the temporary lives as long as the reference。

So the first line creates a temporary object English42。And then， the reference。

Is available throughout the rest of the function。 So the lifetime of the temporary gets extended to match that of the reference。

 So the second line is Ok because the temporary is only destroyed when we no longer can use the reference。

Which is， in principle， nice right that the compiler does that for you。 But you have to be really。

 really careful with that， because the will only triggers when a reference is bound directly to a temporary。

It doesn't trigger when we've got a reference to a reference， to a temporary。So consider this code。

 We've got get strings， which of vector strings。And then we call it and bind it to a reference here。

 we tweak our temporary lifetime extension because we bind the reference strings to a temporary object whose lifetime is going to match that of the strings variable。

 So this is good。😊，But then， the second line。Be binding it to the result of calling operator square bracket zero。

Now， this will also create a temporary object in order to call the member function。But the colloper。

 the subsequent operator， returns a reference。 So if we're not binding a reference to a temporary。

 They're binding a reference to another reference to something that lives as part of the temporary object。

 So a temporary lifetime extension doesn't kick in because we're not binding a reference to a temporary。

So when we reach the semicolon， we are destroying the vector of strings。

 and weve just got a preference that immediately dangles。😊，And the same。So you have to be really。

 really careful when using temporary lifetime extension。

The second case is when we've got temperatures created within the range expression of a fall loop。

 So everything after the column， all temperatures created in there are gonna to live as long as the fall loop。

😊，です。So in this case， we are iterating over all the strings We from get strings。

This is also gonna create a temporary object， and that temporary object that holds our strings is destroyed when we are done with the loop。

 So everything inside the loop can safely access it。😊，Similarly。

 we can isuate over the first string because the vector of strings is a temporary object。

 but then temporary object is only destroyed when we're done with the loop。

So this code is also safe because theres a special exception to the special exception 4 inch best follow。

😊，And this was only added in C+ 23， I believe。 So before that this the first one would work based on the previous rule。

 but the second one is just immediately dangling。But since people has 23。

 both of those are completely fine。 You can safely just use the brainb follow loop whenever don't have to worry about it at all。

 Just forget what I told you。 And you can just use we skin。Yeah， thanks to Nikco for that。

Any questions about temporaries？Yes。sorryrry， there's a microphone coming if that's the wrong question。

Yeah， so I'm aware like this is going to be a bit cursed， but。

So now we had like a function returning a value and bind it to a reference。

 But what if we like change to get strings to return a reference to the vector and then do like， oh。

 return。Vctor， like constructed in the return statement， How long would that then live。

 like I'm not wanting to do that， but of of interest。 So。

 so you've got our get strings function returns a constant reference to vector of strings。

 and we write return temporary vector。This will just immediately tin up。

Because the temporary will until we reach the semicolon of the return statement。

 not of the semicolon on the collar。And I think there is some proposal to even disallow that because this is just stupid to do。

 but yes。In general， just like temporary left extension。

 like for the way followup is nice because it's not obvious that we're creating temps。

 But in all other situations， just forget that temporary left extension is a thing。

 and you're gonna be so much happier。😊，There's gonna be a lot of that coming up in the talk。

 So there's a lot of details， but the details shouldn't really matter for your life at all， I hope。

So let's talk about placement New。Now， an object is created by new expression。

 where there's a special kind of new expression。And the socal placement neural expression。

 which is doesn't allocate any memory， just explicitly calls the constructor。

 So we've got some memory from somewhere。😊，And then we can use placement nu to explicitly create an object in that memory。

 So here we are explicitly creating an in object in our memory and getting appointed to it。

 So we manually create an object， essentially。😊，So place new a to manually create an object。

 start select them and to manually destroy it， you can explicitly call the deor。So we can buy object。

 dot tilde， and then the name of the type。 And this explicitly calls the deor。

And this is necessary when you use Place U， because we've manually created it。

 we also manually need to destroy it。AndThere is some syntax quirk about this。

 So the type name there are in the dis vector call can only be a single identifier。

 So it can't be like int because int is a keyboard。 So it can't find x do tillil the int。😊。

It also can't be a qualified name， so it can't find x tilder stood string。

Just because the grammar doesn't download it。 You can still call the construct using like a type di or using decoration。

 It' just， the grammar doesn't download it。So I will just use the standard library function display it。

It's just caused the deor。And because in this case， the type name is Ob T。

 like the grandma allows it， and we can always write it regardless of what the type is。

 This is just a purely syntheticctic quirk of the language。

 So this toilety explicitly calls the destructor。So in order to call placement new。

 we need some memory for object to live in。So how do we get that memory without having actually created an object。

嗯，没得。Yeah， how do we get that memory， And we can use it me， for example， right， the C function melo。

 It just allocates memory。 It doesn't create any objects。

 So we get a memory we call placement new to start the lifetime of a new in object in that memory。

 And then we can happily use it。😊，Right， so we can start using it。 And then to end the lifetime。

 we need to destroy it。 And then we also need to feed the memory。

And this is the full life cycle of the object just like manually written out every single thing。

A more C plus plus version uses operator U。 So unlike new operator U just allocates memory and doesn't actually create any objects。

 So essentially， the code looks the same with melo。

 we just use operator U and then notice why we use operator delete。😊。

We can also use an array of uns Charles tonight。So here we've got an unsential array that is aligned for int and big enough for int。

 so this can provide storage for end object。So we can then use placement new to create an into object in that buffer and start using it。

And two things to point out about placement new， placement new can be overloaded。

With to do whatever you want。 So if you want to be really careful about that。

 you always have to use the colons in front to call the global version and also have to cast the pointer to void。

 because a user can provide like a placement that takes a pointer to An Sha and does something entirely different。

😊，Then the version you actually want to call。 So to be like entirely correct。

 the obviously has to use the Collins and the static cast of void star when you call placement new C does it just a great language。

😊，So now we've got an inch object。 And then as before we can start using it， we need to destroy it。

 and then the storage gets delocated automatically for us because it's an automatic。Now。

 the interesting thing is this one， we can also reuse the memory of an existing object。😊，Here。

 we got our。It then destroyed。Now， we don't have an in anymore。

We just have some space where an inter objectject used to live。

We can then use statement new to create a new in object in there。And then we can just use it。

And then when the ink gets destroyed， the lifetimes。Now。

There is something interesting about the final semicolon， which ends the lifetime。

Can anybody see what it is。So， yes。Sorry。Yeah， so， so the semicolon， the。

 it destroys the end object of the automatic variable of the first line， right。

 But that one doesn't exist anymore。 We've created a new one in it。 So is this a problem。

I get back to that。But it we can be used in memory way。 But we have to be really careful。For example。

 const is still const。We've got our constant。That's 11。 And this cost。 Now。

 you can't just go out and say， okay， let me just destroy that and create a new one。 That is 42。

That will change the constant value， and that is undefined behavior because constant is still constant。

Mostly。Because when we've got a constant in hip objects， that doesn't matter。

Then we are allowed to do it because for objects on the heap， cons doesn't matter。

 They never really cons。 So we can just do that in this case。

 But depending weve got an automatic variable or static variable。

 we cannot reuse their memory for a different object because that would mean that consed objects are no longer consed。

Second thing is to remember， the compiler doesn't care what you're doing and still wants to destructor anyway。

So when the de has side effects， this can lead to unfined behavior。 So here we having a string。

 were destroying that string。That's good， but then the compiler is going to destroy the string again again。

 right？So this is a doublere。The compiler doesn't care that we destroy the object。

 It's gonna destroy it anyway。 So when we destroy something with a nontri de。

 we have to be sure that we put something in their back and before the compiler destroys again。

 Otherwise， we have undefined behavior。And then we have to be really careful with this code。

 So we've got our int。 We destroy it。 We create a new one。

 We use the pointer we turn from placement new。 That is good。

 That is the pointer to a new end object。😊，What about this line。This uses X， but we've destroyed X。

 X doesn't exist anymore。 And similarly， the destruct in the semi called when we reach the closing phase also destroys X。

 So it's this fine。 Can we just continue using X as if nothing has happened。Well， does then？

After the lifetime of an object has ett， and we get a new object at the same location。

 a pointer that's pointed to the original object， a reference that refer to the original object or the name of the original object will automatically refer to this new object。

If the original object is transparently replaceplaceable by the new object。So we can use X。

 even though we。Did some change we used the memory when we've got transparent replacement。

So what does transparent replacement mean。So A And B is transparently replaceable。

 If A And B used the same storage， which makes sense， they have to be on the same location。

 Otherwise， it doesn't make sense to talk about it。 And A and B have the same type。

 I top level C qualifies。 So we've got our into object。 We destroy it。

 We create a new in object at the same thing。 That is fine。

 That is transparent replacement because there wasn't in before。 There's still an in。 We're good。😊。

So we can just reuse original names， original pointers。

 or original references as if nothing has happened。There are three exceptions， constant objects。

Bace classes at now Unied members。And then then subobject， it becauseively considers it。

 But that's just it， it works out， so。In this case， it's perfectly fine。

Because we have an end object。 We destroy it。 We create a new one。 This is transparent replacement。

 We can just continue using X。Like while that's also going to destroy x。

 This is also fine because x just magically refers to the new object。 which just create them there。😊。

Similarly， this implementation of the assignment operator is also fine。We destroy object。

 and then we copy construct a new one end space。 This is transparent replacement because we have the same type。

 We use the same storagech。And it's not constant。 So none of the exceptions apply here。

 And this is fine。 I note that this changed over the course of C proization。

 the world used to be more strict。So this is perfectly developed by using transparent replacement。

And just to consider the case of subobject。 So here， we've got a member function。

 we destroy our member X， and then we transparently replace it。 and everything just workss up。Now。

 one of the exception was constant objects。Regular con objects can't be replaced at all because they constant。

 but like hip con objects can。So here we've got the constant object on the heap， which we destroy。

 and then we placement new and new one in there。 This is fine because it's a heap object。

 But it's an non transparent。 So when we dere new pointer， which we got from placement U。

 that is okay。 But when we dere the pointer， that is undefined behavior。😊，Because the pointer。

Points to an object that wasn't transparently replaced by the new one。 So the old pointer is invalid。

 even though it has the same address as the new pointer。You cannot use it anymore。

And this is because the compiler sees this code and sees， okay， pointer points to an con object。

And we're not gonna to have a point to something else。

 So the value of star pointer doesn't change because it's a constant object。

And so the commander would like to optimize all star pointer to just the 11。

 because that's the value it has been。And displacement you were destroy would break that optimization。

Which is why it's undefined behavior to use the point again after this。

So even though both points of the same address， we can only use the one return from placement here。

Now， to fix that， we have to use the function some of you have probably beennovating for。 stood La。

No longer it's a magic identity function。 It takes a pointer， and it returns a pointer。😊。

And it doesn't change the pointer， but it magically makes it valid again。

So we can launder our pointer， which doesn't change anything。 but now we can do references it。

Lada essentially tested to the compileala。 I know that it points to a constant object。

 but please forget that it pointed to a constant object。 It may have changed。

 Please generate code again to reload the object。😊。

We're gonna explore exactly how Londa works later on in the talk。But for now。

 student Laer can be used when we are doing non transparent replacements。

 and you still want to be used the original thing。Now， stood launder also helps references。

 So a similar case， now we just tap a reference to the original object， we are doing a replacement。

 We are not allowed to use the reference because it refers to an object that has been destroyed。

 We have to launder the address of the reference。 De you reference it to get a new thing back。

But st la isn't magic。 It doesn't magically prevent undefined behavior。

So when we've got code like this。 So we're assuming int and float are the same size。

 We've got a float object on the he。 We destroy it replacement new and int in there。

 This is perfectly fine。 We've got enough storage。 We've static asserted it。

 but it's non transparent。😊，So。We are allowed to use the eye pointer to point to the ins。

 but we' are not allowed to use the float pointer because it points to a float object。

 but we have no float object。 We've destroyed the float object。

And wrongdoing doesn't help us because we still don't have a float object。

 But there is a float object we can do with。 We are only having a。

 So this is still undefined behavior。So stop La exists， when do you need to use it？

When you want to re the storage of cons heap objects， Because remember。

 you can't use the storage of cons non heap objects。

 When you want to re the storage of base classes or no unique address members。So， in other words。

 never。They're gonna get back to that。 And also know that when Landa was originally introduced。

 The woods were more strict about transparent replacement。

 and there were more situations where you'd have to use Lada。Essential。

 generic called always had to use Lada。 But this was annoying。 So the woods were relaxed。 And now。

 essentially， Lada is never used。😊，Again， they're going to get back to that。So at this point。

 itre going is gonna to start interesting。 So questions about。Placement new and object reing。

I used to follow me。H。Okay。then just jump right to the deep end and talk about implicit object creation。

No。We've got another totalology。 an object is created by an operation that implicitly creates objects。

Thank you。 What's the motivation behind that。Consider this C plus plus version enough C code。

We called Malek to allocate storage from in。And then we just start using it as neat。

According to all the words I've described so far， this should be undefined behavior because they don't have an names object anywhere。

Nothing has created an li object。 So can we just start writing to one who created that force。

But it really shouldn't be undefined the area because that's the way you did it and see and to just continue to work。

 But for like。22 years until C 20， this was undefined behavior。Nobody， like everybody did it。

 but it was undedefined behavior。 And this was just back in the way object creation and life was specified。

 because， as I told in the beginning， like， this is an invented property。

 The standard talks to talks about semantics。 It has no effect on the actual onetime behavior of your code of your code right unless the compiler decides to optimize。

So this was the back in the specification。 This was got fixed by saying， okay。

 some operation implicitly create object。And by alert alert Me is one of them。

So those operations essentially。😊，The compiler is doing something unique。

 When you've got implicit lifetime types like it， the compiler will implicitly create and start the lifetime of objects。

 If doing so would prevent undefined behavior。😊，Which is pretty nice。

 So if it helps you to prevent undefinunded behavior。

 the compiler will just jump in and catch you and say， you're about to do undefinunded behavior。

 Let me fix that for you。😊，Which is like the only instance of the C plus stand up where the compiler does that。

 And all other instances goes， oh， you have any Van behavior。

 Let me just do something entirely different。 But like here， it actually goes at。 It helps you。😊。

So the caveat about the implicit lifetime types is just pretty obvious。 Like。

 if you've got a class whose constructor and deor does something。

The compiler will not intrinsic call those because then this could just silently allocate memory or whatever。

 And you don't want that。 So this only applies to types where the construct and the deor do nothing。

But this is enough to fix the code where we've got like see code Theyre just called Manoc。

So which operations do that， for example， meoc and variants operate a new allocateocator。

 allocate and a bunch of other allocation factors。So the compiler looks at this code。

 looks at the second line where we're using an int object that doesn't exist。

 And because meoc can implicitly create an object， The compiler goes out and says， you know what。

 Let me just create an int for you。So to make this code well different。Bch it's nice。

So we I accomplish the goal of having like C like code is still valid because the compiler implicitly creates an in object without you having to do anything。

😊，Anything that starts the lifetime of an uns child or stood， by way， also creates objects。So here。

 we'veve got a buffer for an int， and then we start using it as an int。

 We haven't created any int in there。 So the compiler hopefully went ahead and creates an int to make this con。

😊，Except that's the idea。 There's actually another buck in the standard here where we have to use the to lada。

I don't want to go into why we need the stood la in there right now。 Just pretend it doesn't exist。

 And it really shouldn't be。 It's a backend the standner。 But for now。

 we have to write the st la in order to get the pointer。

But ignore that the idea we've got some buffer of An Sha。

 We use it as an int so we can just start the compiler creates an int， and we can start using it。

Mem copypy and meu also implicitly create objects。 So here we've got a char buffer。

 A char buffer is not an unsign cha buffer。 So think it doesn't apply the previous exception。

 But when we mem copy an in into it， the compiler explicitly creates an in in the destination。

 So we can start using its needs。 And again， we need to use this La for the same reason on the previous slide。

 Just pretend that isn't there。😊，So this code is fine because the compiler implicitly creates an inter。

 even though we didn't do anything。And then the implementation can let like implementation defined operations probably me up virtual analog。

 So when you want to read like just map somewhere memory where you know your data structured in there。

 you can just cast the point to that type and start using it。

 even though you formally haven't created any objects。 And before C is 20。

 such code would have been undefined behavior。 because you just started using it as if there were some objects。

 even though there weren't any。But now the compilable simplicitylic create an in object in order to make the code valid。

Now， biole dust is certainly useful。It's also pretty bizarre because for starters。

 it uses time travel。So in this code， we've got a buffer that can fit both the limbs and the float。

And then we boil the dice。 And depending on the dice， world。

 we either use it as an int or as a float。Now， it's important that the reintercast doesn't do anything。

 It doesn't create any objects。 It's the first line that createds an object。 So when we， for example。

 want to create use it as an int， the compiler has to travel back in time in order to create an int at this point。

Alternatively， you can say it's quantum mechanics。 And when we create the buffer。

 we simultaneously create an into our float。 And then we we use it as one collapses。

 And we have always created an into float。 But in other cases， it's like pretty bizarre semantics。😊。

And also note that once we've put memes in there。When we start using it。It always is means。

 We can then can't just silent start using it as the float later on。

 That would be undefined behavior。 The cab implicit creates an in and now their choice is stuck。

And this sort of time travel semantics is only possible because like， again。

 for the the CPU doesn't care。 Like， it's not something that executes an actual hardware。

 just some semantic fix for the standard。 And again。

 the lawn does necessary because of the thing I will get too late。And just like stood Lana。

 implicit object creations is not a magic thing that prevents all undefined area。😊。

So when we use code like this， where we got our int and we reintrot customer to a float pointer。

 the compiler will not create a float for you。So this is still undeified behavior because we are dereencing a float object。

 but we don't have a float object。 We just have an object。是。I'm sorry。

Tool to reveal when your compiler creates objects for you。 something you could actually see。 Yeah。

 so it the。No， but it's just the situations I've listed。Imlicically create objects。

 And like some implementation defined functions， which also allocate memory。

 will also do that for you。But its also it， it doesn't really。

 you don't really need to have it revealed because by definition， it doesn't do anything， right。

 it only applies to pre lifetime types because otherwise。

 we would get in trouble with actual time travel， which isn't implementable。I think。So。

This is all good。 But consider a cut like this。 So we've got a person that we get some buffer。 And。

 then we want to start using as as a。😊，And it， this might be undefined behavior。

Depending on how we get the buffer， like， if it's from one of those magic places where the compiler will time travel back to and create the int。

 we're good。 But we don't know that because it's just a function。😊，So we want to make sure， okay。

Please always get me an in there， even if when one of the situations where we wouldn't have gotten end otherwise。

And you might be tempted to say， okay， we do placement new。

 So we placement new inside the Bufffin it。 And now we've got an。Well， this is very defined。

We might not get the same volume。Because even though the placement nu for the int doesn't。

 the initialization doesn't change anything。Physically， semantically， it changes it。 Semanically。

 it creates an entirely new object that has nothing to do with whatever was there before。

And so we don't have any guarantee that this is a no up and doesn't physically change the bytes。

So even though this is well defined， we might have 11 in there and now we might have something entirely different in there because placement new changes that we've created a new object。

 we've lost the property。What we want， yes。No。don't see your sister。Cost。

That so be steady casting and。Now， the， the the placement new at the end。

 the placement new of Is returns an instar。So this always has to quick type。 And then we， oh。

 and then we're casting an un sharp pointer to avoid star。 But this is a static cast。Yeah。Yeah， so。

 so， yes， yes， this function assumes that there's an in in there。

 but it's also fine because we're explicitly creating a new wind。😊，At。This just gets some memory。

 It assumes it's big enough and creates in India。This doesn't read the existing bytes in show that doesn' an in。

 which is what we actually wanted to do here。So what we want to do is we want to say， okay。

 we've got this buffer。 Let me create an int in there， but please don't physically touch the bytes。

And for that， we can use to start lifetimes。This takes a pointer and a type。

 and it will turn your pointer to an int in this case， whose lifetime has started。

So now we are taking arbitrary bys and we are starting the lifetime of an in objectject in there and reads whatever the bitete values were interpreted as an int。

 And this is well defined behavior。😊，endSo when you want to write code， for example。

 you're doing socket I O。 and you've got some bytes from the socket。 And you want to say， okay。

 the other side send me this data structure。 you can use stood start lifetime S with your data structure and say this is my data structure at no this in the bites of the socket。

 And you've got completely well definedfin behavior。There's also a version for A。

 which takes like a dynamic cut。And yes。Sorry， there's the microphone coming。

What's the difference between start lifetime as versus reintert cast？

 So the we soet cast is only fine behavior。Potentially， in all cases。 No， so if you've got in object。

 you reintercast to Anch and then you reinter cast it back。 that is fine。

But if you've got something that isn't in object， then it's undefined behavior because you're using the object without one that has been created。

And stood start Life S always creates an in object for you。 So this code is always very defined。

 It doesn't matter what lived in buffer before。😊，So if there was a float in the buffer and so if there's a float in the buffer。

 you will then reinterpret cast the float as an inch， but without undefined behavior。

I will get back specifically to the float in example later on。 when we talk about typepan。 Thank you。

 But this is just code。 you， for example， like， as I said。

 you've got bitetes from the socket coming in。 You know， this contains some data structure。

 You start the lifetime of that data structure， and then you can just use it directly。😊，嗯。嗱。有。

But like。So let's assume I have like a float pointer。 and I like give it to this function。

 Like there's a float typically living in there。 And now it's like start lifetime as end。

 and then I return， like， is my float now broken。 I'm gonna talk about that when we talk about。

For now， in this case， assume that we've just got bytes。

 and we want to read those bytes as an int because they come from network。

 They come from fire mapping。 Then you can use to start lifetime S to get value behavior and start reading them as some ins without having to touch them。

😊，Okay， sure。In all your previous examples， you've deliberately aligned the storage beforehand。

 But here， what's the alignment of buffer and could be wrong。 Yes， so。

 so this code assumes that the buffer is big enough to hold an end and' probably aligned for end。

 Otherwise， you will still have antifin behavior for the other reasons， yes。Okay。Now。

 still start lifetime S， just like St La is a magic standard library function。

 but we can actually implement it sort of。😊，So this is a potential implementation of start lifetimes。

We do a memo of pointer to pointer size of TBtes。So this is an hour， like。

 it doesn't move any bytes because source and destination are the same。 But remember。

 Menmo implicitly creates objects for you。So when we returned， then a point to T。

 which we might have to launder because we don't know where it came from。

And then later use it as a T。 The compiler will travel back in time to the mammoth and create a T object in there。

😊，So， that way we get the。Implicit creation of the object without having to do anything。

 The standard library implementation is an actual nowup。 It's just a compiler intrinsic。

 and it also works for cons。 This one like。😊，Doesn't like constant。 But like essentially。

 we can delegate to the memo thing。 This isn't useful to know。 It's just cool。

So we've got implicit creation of objects。 There's also the flip side。

 implicit destruction of object。Because even though we can call thisto to explicitly create an object。

The meA act of releasing storage or re using storage also did destroyise objects。So in this code。

 we don't need the destroyy a for the。Because just the act of calling placement new ends the lifetime of whatever was in there and starts the lifetime of a new thing。

😊，Similarly， then we've got our unsial buffer。This starts the lifetime of an unsanch way。

And when we call placement new on there， this ends the lifetime of this uns cha away and instead starts the lifetime of N。

😊，And then we can use that pointer。And we also can't use the buffer anymore as is。

 because we don't have an answer shadow away anymore。 We just have an in object。

And because the lifetime of an object ends just by releasing the storage， or reus the storage。

And this means that memory leaks are not unevenfant behavior。

 So here we've got the stood spring replacement new new string in there。

 This ends the left of that spring object， but it doesn't call the destructor。😊。

So we've got a memorymo leak， but this is perfectly fine。 This isn't unfined behavior。

 It's just a memorymo leak。And then we use it。And again， we will destroy the string object。

 but this will destroy the new string because we've got transparent replacement。

So we've got some situation maybe implicitly create objects。

 You can use to start lifetime S to explicitly create objects。

 and we can implicitly destroy objects just by using the memory。😊，Any further questions？

Out this part。Okay。So let's talk about provenance。Consider this code。We've got two inter objects。

 x and P。Why is 11。Then we do something with the address of x。 And then we return y。

We expect our compiler to optimize that return by to return 11。

 because by is 11 and nothing changes by。But what if do something does this。

 So do something takes the pointer， gets one further and sets us to 42。😊。

And it might just happen that whatever this address is， is the address of why。

So now we're changing y in this function， So the optimization is broken， right？Well， no， because。

We don't know that like， this could be some arbitrary address。 So let's say we do that。

If the address of Express one is the address of Hawaii， we call do something。And do something。

Modifies the what stored as address F x plus one sets this to 42。

 And we know that this is the address of Y。 So this sets by to 42， right。😊。

Which means that the return 11 optimization is definitely important。

Because if we reach this condition。Why has been set to 42 by this code。

 Because that's the address of why that we're sitting here。Right。

Except the optimization is still valid。Just because two pointers are equal。

 Just because they point to the same address doesn't mean they point to the same object。

They're not interchangeable。I'm going to say that again。

 just because two pointers are equal doesn't mean they point of the same thing。

This is because a pointer is two things。 We've got the address。 This is the filter thing。

 This is what's being compared， and it've got something called provenance。

And the provenance identifies the object or location the pointer came from originally。

And the pointer view reference is only valid。 If the address is in the allowed range of that allocation。

 as determined by the provenance and the current provenance of that address still matches the provenance of the pointer。

😊，And， crucially。Pointer Ametic doesn't change provenance。So let's look at the example again。

So it compares X plus  one and the address of I， this compares the addresses。

Even if this returns true， the provenance of point up plus one。

Isn't the same as the provenance of the point as why。

So we can't dereence it because it points to memory look like the address isn't in range of the allowed provenance。

 So pointer has a provenance address of x。 And that provenance doesn't allow the of point up plus one。

 because it's the invalid address range。😊，So this is still un definedfin behavior。

 even though it has the same address as another object。 we could modify。

 Were not allowed to do it via this pointer。And this is crucial for the compiler to optimize that to return 011。

Because it is that the address of I isn't。Nobody does anything with the address of why。

Nobody can change it because the only way to get a pointer to Y is viado。Taking the address of it。

 we can to point athmetics to randomly get it。And similarly。

 we can to reinterpret cast units and point us some number to get why。

Because that would have the wrong provenance。And this is also related to Lada。

 So here we've got our constant object allocated on the heap。 This is provenance A。

 We then destroy it。 We then create a new object because we are having non transparent replacement。

 This has provenance B。😊，So when we use new pointer， it has to correct provenance for that address。

But when we use pointer， it has the wrong provenance。 It's still provenance A。

 but the object has provenance B。 So this D references unde behavior。We have to learn that。

Because what lawner does， it detects the advers and fixes the provenance。

It keeps the address unchanged， but sets the provenance to be。

 because that is the currently valid provenance of that address。 And then we can use it。

And the same thing also applies to references。So reference also as provenance。

It has the provenance of the a object。 So when we replace it， the provenance is wrong。

 So we have to launch that。So provenance extends to Gunder。 Every object has a unique proven。

 except in a way， Then they all share the same。 So you can use pointer automaticmetic within in a way。

😊，And reusing the memory of an object changes it if you don't have transparent replacement。

And if you use to learner， you can update the provenance of an object。Questions about provenance。

Its bit yes。In the very first example where you said dereencing p plus1。I UB。

 how does the compiler figure out if that pointer is just an integer pointer or pointer to an array？

So how does the pointer figure it out。 The compiler doesn't need to figure it out。 So the compiler。

 the function do something is fine on its own。😊，Because this might be called bi an A away。

 And then it's fine。 Its when we call it with the address of X。 Do we trigger the unfined behavior。

And so the compiler looks at both functions in isolation。 It see， okay， this one。

 we're just doing a store。 This could be in a way。 This could be fine。

 And then we look at this function。😊，The biology is， okay， we've got Y。 We said y to 11。

 then we take the address here， but we don't do anything with it。

 And then we're just doing something with x， which is all good that because of provenance。

 this can never modify y。 so we can optimize this to return 11。😊，And at one time。

 we trigger unde behavior， but this is't only detected when we see both functions in isolation。To。

 when we see them in isolation both codes is fine。Thank you。😊，Because again。

 like provenance is all purely a semantic thing for the standard。 Like it doesn't。

 It's not in hardware。No， that's best of W day。Okay。So with that in mind， we can look at typeaning。

So we're assuming the remainder of this section in and flow of the same storage as before。

 We've got an in object。 We create a pointer to it。 This is fine。😊，Then we've got a float。

 Then we reintro broadcast that pointer to point at the float。That one is also fine。

The problem is the last time we we do were friends to floor button。

And this is something deal do with strict aliasing。And colloquially， we'd say that， okay。

 you can't be interpret cast between unrelateded types。But more this is wrong。

 we can do with the brain robotcast。 What we can't do is the access。

 So if a program attempts to access an object to an L value of a type that is not similar to the type of the object。

 we have undefined behavior。So you can't access an object to a pointer often type。

 In the previous slide， we've got an end object。 We're accessing it to a pointer to float。

 This violates this rule。 But merely having the pointer is fine。

The type of a point or reference is irrelevant until we access it。

We can freely reinterpret cars between point us as long as we want。 But as soon as we do referening。

 they have need to have the correct type。 Otherwise， the type is entirely irrelevant。

So this brings me into this code。 somebody alluded to that not quite， but similar。

 So we've got our inter objective。We put a float in there。 We've got a pointed to that float。

 We can use that float。 This is fine。 We can't use I anymore because this is not transparent replacement。

 We don't have an inter object。 We have a float object。

 We can't access an a float object by an into object。

 This files tick A think this is unfined behavior。😊，Similarly。

 this is what somebody mentioned earlier。 so we can do stood start lifetime as float on the end object。

 Then we got a point to a float that happens to have the same bites as the int。 and we can use it。

 but we can no longer use the int。We've ended the lifetime of that in object by replacing it with a new one。

So as soon as we do start lifetime S， the original object at address ends。

 and we can no longer use it。So if you want to do some bit of type planning， right。

 and don't care about the original one， you can use start lifetime myth。It's a bit weird。

 but it's fine。 Like there's not only fine behavior。Yes。

Could I use Do Life thumb as a second time with the end。Or with a flow to get the ink back。 Yes。

 that'd be possible。 Yeah， you can use not。So I don't think so。

 So if you do like a stood start lifetime S。 So on on the Fer。 like on the yeah， yeah。

 if you do stood start left us the F pointer I don't think I itself is valid again。

 Okay because we could do a non replacement。 and then another non replacement。

 And I don't think this tracks through that。 but what you can do is lada。

 and then you can start using it again， just the provenance itself has changed right So we've got provenance a for the in。

 then we got proven B for the float。 we create the in back we got proven C。

 right And so we cant can no longer use the name But in principle。😊。

It's a pretty weird way to do typeing， but it would be fun。Yeah， I mean， this is essentially。

What I mentioned。 So we've got our fl pointser here。 Al ready。 Then we do the placement U。

 That flow point has one。Even though it has the correct address， it has the wrong provenance。

 That has the provenance of the in object。So we cannot access it。Directly。

 because of test among provenance， right， And I get like。

 this is weird if you don't know provenance because you've got to point out to the correct type。

It points to the correct address。 And we have an object of that type， at that address。

But we can't do reference pointer because we got it the wrong way。

And it doesn't help if you do it in this order。Right。

We still got a pointer that points to an now destroyed in object。

So we can't use it because it still has the provenance of the old end object。

We have to either use the point that we get from placement you， which gets the correct provenance。

Or we have to learn that。This is like， really subtle。But I hope him makes it。

And this brings me to the back in the standard。This also applies to An。Buthich is very unfortunate。

 So here we've got the un cha buffer。 And then we we reinterpretcast as an inpointer。

And even though the compiler would happily create an end objectject in that buffer for us to make it valid。

 we don't have a point with that in object。 We have point with the un child object of the wrong type。

😊，So this is unified behavior because we are just having a weird pointer to an object。

 not a point to an in object。 And this is just a backend the standard。

 Like there is some wording in there that says that this pointer has the same provenance as any object created inside the thing which this paper adds。

 But until that wording is added， we have to use lada。😊，And again， like， this is a spec。 like。

 this should work because otherwise the entire rule list doesn't make sense for the implicit object creation yeah。

嗯。So this is the final city as Mary might want to use towanda。

When you want to reuse memory and store it for a different type， you have to learn it。

Especially with Anschar， but that's going to be fixed。So never used to floda。

 but terms and conditions may apply。手掉啊。2 exceptions for the strict aliensing order。

 The first is we can always access a signed or and version。 So when we got our int。

 we can exit this as an un。 Even though we don't have an non in anywhere， we can do that。😊。

Which is nice， I guess， I don't know。The second one is more interesting。

 we can exit this as a cha and central stood bite。Now， the idea here is that remember an object。

Aqui storage， which is just a sequence of bits。 And we want to print those bits as bytes so we can iterate over it as a st by and print out each individual byte of the object。

😊，This is why the reintrot cast exception exists。Unfortunately。

 there's another bug in the specification， which makes this entire code undefined behavior because we're doing pointer。

😊，Athmetic。But we don't have an array of bites。Anywhere， so we can't do pointrithmetic。And like。

 this code's meant to be valid。 It was valid in the past。

 but it got fixed by like got broken by drive by it change to something else。

 And there's another paper to address this。 They're just trying to figure out the wording to make this valid again。

So。You know， you're like pretty deep and you find ps and the C best standards for the sort of woods。

So more explicitly， to somehow， we can do type hunting with that left。

The reintert cast is un behavior because we don't have a float object。

 But when we create a float object， we're good。But we can't use I。

Because they don't have eye anymore。 Like， we don't have an names。 We've got a flood。

The other famous way to do Taip is via Union and this does not work because of the final。

A phrasese in the sentence and object is created when implicitly changing the active member of a union。

So we've got a union of Interfl。We create an int。 We create a float。

 This changes creates a new object， destroy at the same address as the int。

 So we destroy the int object。 So we've got a float anymore， but no in。

This is unified behavior because we're accessing an into object that has been destroyed。

By reusing the storage by a phone。There's one exception。So when we got two standard theres。

In a union， and they both start off the same list of members。

We can access those members that are common in both variants from either member。

 It doesn't matter about the active bonus。So here we've got a union with A&P。

 both A&P start with an in。😊，This is in the common initial sequence。

And then it doesn't matter whether were right you do A prefix or U do B prefix because both have prefix。

 right， We can just access it， however we want。Now， this is not related to lifetime。

 We're not changing the lifetimes of anything。 It's as the second line U dot dot prefix。

 It's as if we have written U a dot prefix。 The pilot just automatically change it to whatever is to correct member access to make it valid。

 So this is just a convenient rer tool that we're getting into one time。

 This is nothing to do object lifetime。 But it's pretty convenient。 So， for example。

 when you have a tech union， you can put the tech inside eachstruct variant as the first thing。

 and then you can access it directly and save a bit of alignment in some situations。😊。

We can do typinging via studentm copy。 And again， this is because we've got an into object。

 and we've got a float object。 And we're just copying the bytes over。 right， It's non controversial。

 We've got a float。 We've got an in。 We just transferred the bytes。😊。

No a lifetime business is going on you。The more button way is to use Spitcast。

 So bitcast is essentially a context per me copy that just works。Yes。Yes。

 the the same I did a static assert a couple slides ago that still applies here。Now。

 there's one final exception where type planning also works。If you've got the standard layoutstruct。

With one or more members。We can do the following。 So we create a construct object and then we get a pointer for the first object by reinterpret casting the a。

 thestruct object。 This is always fine because we can always reinterpret cast。

 But we also also allowed to de referenceence that point。😊。

Even though that pointer points to an A object and not to an in object。

 because the A object starts with an in object， we are allowed to access it。

And we can even go the other way back and reinterpret cast the pointer to the first member。

 back to the parentsstruct and access it。Yeah。Hi， in terms of the standard。

 then the concept of being transparently replaceable， if you have a base class。

 which you can convert to a derived class， is that technically transparently replaceable or is that a work And no。

 because the transparent replacement exception was， you can't do it base classes。

Because then you get into V table business。And stuff like that。 Okay， sure thanks。

So this works because there's a special exception。 The pointer interconvertible exception。

So if two objects are pointer inter convertverible， then they have the same address。

 and you can obtain a pointer to one from the other by a reinterpret cast。

 which means that essentially the address of a and the address of a dot member have the same provenance So we can just get a pointer through one to either one。

 and it doesn't matter。And it applies to。The same object， obviously。

 but also unions and their members and standard level respects and their first member。

And then it's transit。And the fix for the unsigned child buffer stood long the rein would also add like what another condition to say that an unsed cha buffer。

And any objects created within it are point out to convertible to make the reinterpret customer work。

 But it's currently missing the wording。 So it's still undefin area， yes。

I don't know if you're covering this in following slides at Does this also apply to in classes with regards to the。

 their underlying types。 no， this does not apply to inum classes and the underlying types。

 I this the full。Butdding， okay， for the。Yes。上。Let's end this talk by talking about invalid en zombie pointers。

So excess of an object outside its lifetime。So before the lifetime of an object has started。

Or after the lifetime is ended， Any pointer can only be used in limited space。Similarly， any。

A reference or the name of the object can only be used in a limited ways。Essentially。

 its like a bunch of protein that follows， but essentially。You're fine to use pointers。

 but you can't dereence them。Which makes sense。 So， for example， we've got an object be described。

 We can form a pointer to it。 We can even form a reference to it。

 We can form another pointer from that reference， or we can form a reference from that pointer。

 This is all valid because we don't exist the object anything。

 We're just creating different names and different pointers of it。

And then we can also compare the pointers。 Pointers have to be equal。 This is all valid。

 Even though we don't have an object anymore， we are not accessing it。But as soon as we access it。

 we've got any behavior。So we read the value。 we dere the point out。

 This is obviously unified behavior because we don't have names anymore。

So we've got undefined behavior when we use such a point of reference to access the value。

 to read its value to write its value。To call a non static member function。To delete it。

Or to do anything with virtual based classes or dynamicist。Then the object has to be alive。

Which seems pretty intuitive。 right， You can compare the addresses of these destroyed objects。

 You just can't do your enzyme。 This makes sense。Now， there is one important exception here。

 This will only apply。After the storage has been allocated and before the storage has been delocated。

Because if you access a pointer。To something that hasn't been allocated anymore。 Now。

 things are going get interesting。So this is correctlyly called the pointer lifetime endZP。

So when we reach the end of the store situation， all pointers that have addressess inside that storage situation become invalid pointer values。

😊，Indirect of them， so referencing is undefined behavior。

 and any other use is implementation defined。Beach can include trips。What this means is。

That in this case， we've got to objects on the deck。 We create a pointer to it。 We destroy it。

 We can obviously no longer dere part out， but we can still compare it。

 right It's not going to be not。That when we've got an object on the heap， and we delete it。Now。

 pointer points to the allocated memory。Which means that the compares to null finder is actually implementation defined。

Which means the compiler can insert the studentboard here。When we compare our point。

Which is very interesting。 So why does this happen， Well it's， again， compile optimization。

The compiler would really like to assume that every time you call new。

 you get a brand new pointer that the world has never seen before。

This makes alias analysis a lot easier because you don't have to worry about the allocator reusing storage。

But the elevatorequator is obviously gonna re stch。

So we just make the comparisons and implementation defined。

 so you can't really observe that in the standard confirming problem。In principle。

 we could also do some safety stuff。 For example， we could have delete of a pointer can set it to model。

This would be a valid implementation。Because the comparison of N plant is implementation found。

Similar， but when you've got a function that returns like a pointer to stick to its stick memory。

 which would then be delocated by the time we get the pointer。

 This could also be become node pointer。 So anyway to return local address。

 this could be translated into return nu pointer for safety reasons。No implementation does it。

 but it would be a lot。Now， this behavior。Of invalid pointers。

Has pretty interesting consequences when we consider multi threadreading。

So this is an example I've taken for of paper， but we've got a link a stick。And multi threaded stack。

 So we've got a singlely linked list of node， and each node has an next pointer。

 And then we've got a push function， which gets the current top。

 sets the node next pointer to the current top。 And then we're doing compare exchange。😊。

Loop until we finally managed to correctly set it。 So if by the time we between getting the top and setting it。

 some other third could have changed the top， in which case we have to try again until we correctly set the correct thing。

And then we've got pop all， which simply take sets top to all and returns the entire list to some to do whatever it wants with it。

No。We can imagine the following execution。 So we've got a list containing of a single note。

 note one at address A。Then we've got one threat。1 thread allocates now， too。 It has addressP。

It executes all top equal stop。And sets new node next to L top。

 So now we've got al top pointing to node one and node 2 also pointing to node  one。I got。

But unfortunately， now another thread comes in。This bet executes Paal and delos Note1。So now。

 all top and now two points to the allocated memory。

Which means that when that T does the compare extension week， there was this implementation effect。

Because Utop is an implementation defined find value。Thed memory， this may or may not succeed。

Or trap or do whatever。And as long as the implementation defines。We're just bet。

But it gets even worse。Consider be in this situation。There are two deleted note one。

It now allocates another note， which happens to reuse the same memory。And successfully pushes it。

So node top points to node 3 and our top points to node 1， and node to next points to node 1。

Then the compare exchange week is also implementation defined because U points to thelocated memory。

Logly。It has the wrong provenance for the as the different top。 And like。

 what can the comparison do here， Because if the comparison says it returns true。

 they have the same addresses。We've got the one provenance in there。

Noe2 next has the provenance of node 1。 So if the comparison returns to。

 any axis over the list will be unfinifieded behavior because we're not allowed to deal with node to next pointer。

 It points to the wrong thing， even though it has the correct address， it has the wrong provenance。

So they compile us to return falses， but that's not implementable because the provenance isn't stored in the pointer。

This is just a one term property。 so nobody can correctly compare the provenances in there。

So whatever we do， it's sort of screwt here。Right。Yeah， this is a backendacy fast enough。This is。

Leftly debate about how to solve this one， because on a hardware level。

 it doesn't matter at all because on a hardware level， none of this provenance。

In point of values has any effect。 But like in the specification。It has an effect。

 And according to the specification， we can't write this code。Now， the solution from the paper。

 if you taking the example form is to say， okay， comparison if invalid point of videos is meaningful。

 It does what you expect。 Implementation isn't allowed to silently change those bits。

And then we need to use some la mechanism to automatically update the provenance of not just the pointer。

 but every pointer reachable from that pointer。And this is a bit bad for optimizations。

 because as soon as one of those functions exist， the compiler can't do a lot of optimizations anymore because it has to assume that this function gets called all the time in code they can't see。

All right， so this isn't ideal。And yeah， like， that's back in the C standard。 It's just purely deing。

 doesnn't allow this sort of behavior。And on that note， I end the talk。

As some personalson guidelines。Don't feel animplicit object creation。 right， By nice， It's weird。

 Like， we've got the time travel behavior。 It's not obvious when the happens。

Just use placement nu to explicitly create an object。Like。

 this makes it clear we're creating a new object here。 We don't care about the previous values。

When you do care about the previous values you to start lifetime S。

 So you em up your memory that contains your data structure。

 Call to start lifetime S to get a pointer to that data structure and just start using it。

 right It makes your code more expressive to use。😊，Whenever possible。

 use the pointer from placement new and start lifetime as directly。

Because that pointer is guaranteed to have the correct provenance。

 Then you don't have to worry about their transparent replacement roads。

 You don't have to call st Lana。 right， Just use the pointer they give you。In some cases。

 this isn't really possible because it would mean storing an extra pointer and your stood vectorto。

 for example， because you need the correct pointer。

 even though it has the same bits at the other one， then you stood la。

 it inhibits compile optimization。 But otherwise it does nothing。

 So it's fine to also call stood launder in cases where you don't need to。

 It's like it's gonna be fine。😊，And instead of N cha buffer use a union， right？ So for example。

 stood optional， It install a T or nothing。 You can implement it using a union on An buffer。

 but the buffer， you get into troubles with back in the standard might have to use it longer again。

 it also exp use the union of a cha that is empty and T。

 And then you follow the typea and it makes it easier。

 Like all of those details about implicit object equations are kind of nice。

 but we've got this explicit functions。 And like I think C would be a better language。

 if you didn't have to worry about whatever the implicit semantics we got to support code we just have explicit synt to create objects start the lifetime。

 not create the objects and so on。😊，And with that， I'm done。 So I work at things。

 as you can start from the logo。 were also hiring。 So if you're looking for a job。're hiring。

 I've got a bunch of mech like I've got socks and raincoats。 I can hand out afterwards。

 I'm blogging now at the things Ill develop block。 So if you know my blog before。

 the slides will be available at that URL。 the website doesn't exist yet。 I create it。

 So if you're watching this on YouTube， you can go to that URL otherwise don't。😊，Thank you very much。



![](img/56fba6d34face213c80b8ac2ab581eec_4.png)

![](img/56fba6d34face213c80b8ac2ab581eec_5.png)
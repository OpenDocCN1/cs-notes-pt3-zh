# 【Jonas-Birch】用C语言编写一个TCP服务器库-｜-Code-a-TCP-Server-library-in-C--BV1TBCyB7EU8-

What if you wanted to create a TC P server， And all you had to do was this。 You select the port。

 choose a function， which is going to run every time someone connects。

 Then you can just check if it succeeded， Otherwise。

 you can use this error function to print an error。And then you just run listen。

 and this is the entire main function for a TCP server and inside of the handler function。

The one is that's going to run every time someone connects。

 you just send data and you receive by using the receive function and when you return from the function。

The connection is disconnected。 So this is what we're going to create today。Let's get started。



![](img/bff847de8a22c1f9128f39b7d601c680_1.png)

Sub guyss， welcome to today's show。So today， I want to create a small project。

But it's gonna be a TC P。Server library。 And I want it to be beginner friendly。

 I w to make it very easy for any C programmer to create a TP server。 I will only have one exported。

Function， let's say we have a variable called serve。And we said it equal to TCP server。

And this is going to take two arguments。So the first is the port number。So let's say80。

80 or something。And the second argument is a function。 And it's gonna be called like this。So。

We will have a function called Hand， which will take care。

 So every time someone connects to the server。This function will run and take care of that connection。

So the only thing， the user of this library， the programmer。Needs to do is create this function。

 handling the connection。And。And specify the port number。

And the underlying library will take care of setting up everything， making the process。

Go into the background。And。Listen to the poor and everything。

And then you will just use a method of this serve object。So， if。Serve returns true。 So， So we。

 it was successful。Then we will do something like serve。I don't know。Listen or something。那 that这。

Then this function will handle the main loop and everything。And this is the whole main function。

 basically。And this serve needs to be somewhere。Let's say we have a variable type called server。

 So that's the general idea。And。So it should be beginner friendly for using the library as a programmer。

 The project itself is going to be beginner to intermediate。And it's going to be a small project。

So only these two functions， basically， may be some utility functions that the programmer will not use directly。

And。I want this project to be a one episode project。 So after this episode， it should be done。

That's the general idea。 Anyway， I hope I will succeed in that。And。

And this could be a great project for your resume， or whatever。



![](img/bff847de8a22c1f9128f39b7d601c680_3.png)

。Alright， so let's see。 I'm gonna create three different files。

And we we will not be using any dependencies or。呃。And yeah， libraries， not even my own。So。

And I'm just gonna gonna call this project TCP server。 So we'll have a TCP server dot C。来首。

We are going to have a TC P。No。😔，A TCP server dot。H。And a very simple make file。For comp apping。

Everything， so basically， I will do just do something like。So we want to create T P server。

Dot o from TC P server dot C。And I wantna run GCC。TCP server。Dot C， dash O TCP server。

 And this is temporarily because I will not create a regular executable when we are done with this project。

 It's going to be a library。 But this is during development。So when we have， by the way。

 we can even do。Let's see。I think I wanna have a possibility to add some flags， at least。 so well。

Add this variable here。And。And I'm not gonna do it like， oh。Not gonna do it like this。 I'm gonna do。

Dash。C TCP server。See， so we create an old file。 and then we will have the actual executable。

Which will just run Gcc with the flags。It's going to。And it's go you need。Yeah。

Depenency of TC P server at all。So， T P server。All is going to be TC P， Sir。And all is going to run。

TCP server。And we'll have a clean， which will just remove the old files。Oh， NC P server。Bary。来 so。

And just one more thing， we need to set this flags variable。Yeah。Let's set it to。Optimizations and。

Extra error messages。Alright， simple enough。Yeah。And our C is going to include our O。So， Ill do。Yeah。

Well。I guess we will do this。 Tis if he a bird dot H。

And then we need to modify the make file and add that our includes should be。The running director。

Like， so。Inside of here， I'm gonna include as little as possible。

 but I at least want to have some stuff during development， at least。呃。As to the live as well。

And I'm going to create some integer types， as I usually do。So we're gonna take the unsigned。小二。

Which is our in8， our 8 bit integer。Gona have an unsigned short in。It'ch is at 16。

Unsed inked is in 32。Unsigned。Long， long in。Is in。64。

And then I'm gonna create my regular type casting macros。So。This is going to convert to a jarr。

This to an integer。And then， we have。The one by。Which is an in star。We have。A2 byte。

 which is an in 16。 and we have a。4 by， which is in 32。And an 8 by。 I don't think I'm gonna use that。

 but。Let's have it for completeness。Okay， since we're going to create library。

 we also need to define what we're gonna export and not。So， I need to create some。Well。

 we're gonna have a public。Which sets an attribute。And this is。

Let's see if I remember how to do this。 B C， B Lee。C。😔，嚟啲细听。😔，So visibility， either。

 either it's hidden or it's。嗯。

![](img/bff847de8a22c1f9128f39b7d601c680_5.png)

Let's see。😔，对。Tling。So maybe we have it inside of S。 No， not inside S。 You but well， maybe。

I think we have a day in our ping。 So ping dot H， no。Yeah。Visibility default。



![](img/bff847de8a22c1f9128f39b7d601c680_7.png)

Its。And then， we have。Private。And that is hit。It's hidden， and it's。Stud。Like guess。

Need to have those underlines on both sides。O。So we're gonna have， let's see。

 we're gonna have temporary main function。 and I will indicate that we're doing a space in between。

 in before。嗯。Let's not have any arguments to this。And then we are going to have a public function。

Which is going to return a server pointer。And it's going to be called TCP server。😔。

Taking two arguments。1 is an in 16 for the port number。And one is a。Callback function。

So we need to define what a server data type is。And what a callback data type is。So。

 let's define that。So we're gonna create the structure。So， struck as server。And we need to have。

In 32， for the socket file is characteror。Let's call it F D。嗯。And we。

Probably gonna to need some other stuff as well。 But let's start there as we have something。

And we're gonna type if this。Struck a server。 And this is going to be a server。いそ？

And what about the callback。That is， that's gonna be a function。So。

Let's first define an example function。 So let's say p that。系啊。I don't know。1am。

So what do we want to have as arguments here。I guess。It will be interesting。Let's see。😔，Yes。

 if we could have another structure。So， strong。Yes， let's call this connection。And it， too。

 is going to have a socket file descriptor。It's gonna have an I address。

And how are we gonna store that。I think。Xhiili。That I w to store this。As string。

Just make it easy for the user。So， let's say this is。hos。An I P address needs 16 bytes。

Let's also provide the port number。The local port number， that is。哦。What else。Well。

 that's enough for now。We're going type this。Let's call this connection。

So our temporary function is going to。Provide this connection as an argument to point to their connection。

And I think that will be all we need。Yeah。So how do we define a function pointer。For this。嗯。

So it's going to be something along the lines of。m。Let's see。 Why do we want to return。

Don't think we need to return anything。So let's make this a。And this is a callback。

And we're gonna have。One argument， which is a connect。So I think this would be the syn tack。

Something like this。All right， that's enough。Preparations。Let's start the coding。

So we'll have a simple main function。And here， we want to have a server。Serve。

Which is going to be equal to TC P server。And we need a port number， let's say，85，85。And we need。

A call back。And I'm not sure why I wanna do it like this， but。I do。So， let's say we have。

A call back like this。 So private。Void。Call back。返行。We can call it a handler。Prime。

And it's going to take a connection。Connection。Kong。😔，Something like this。And I'm gonna have a。

Function definition。I mean， a function based macro， which I'm going to call handler。

Without arguments。 And that is just going to return handler pride。Like so。

And then I can say handler like this。All right。If we don't have a serve。

 we will print an error message。 Let's just do this。And。Maybe we could do something like this。

 instead。So， if serve。Okay。Then， we will pray。Error， and then an error message。

Which we get from serve dot。嗯。That's quite nice。Something like this。Exererve， and。S working。Mmhm。

Yeah， Sir。Not， okay。Tin。And if we get this far。We can print something like。Listening。2。😔，Poor。This。

85，85。And then， we'll just do。Return。Serve的。And listen。Alright， this code is。Pretty simple。

 I think most will understand this code。And that's the general idea that this library is going to be very simple to use。

Right。So how do we make this work， The first thing we need to do is this TP server function。

 which will set up everything。And that's going to be the most。Well。The， the function。

 which is going to be most difficult to understand for beginners。

 But it needs to be done in a certain way and。So we can't get around that。

 but the rest of the code will be pretty self explanatory。So， let's see here。

So we're going to have a pub。Function which going to return server pointer。Yeah。TCP server。

It's going to take it in 16 port， and。Cool呗。傻 b。Something like this。

So the CB is the function which you going run。呃。When we get a connection。Alright。

 so how do we set this up， We need to have a couple of things。 First， we need to have a。

Sed integer for the return values。So， let's call this。Right。

And we need an in 32 S for the stocket file descriptor。We need to have a。It stress。So address in。So。

Okay， so in order to set up a T in incoming TB connection， we need a couple of things。 First。

 we need to run socket。 so we get。a soet file descriptor。Then we went around a bind。Which。

 in this case， connect。This。Soet file descriptor to a specific port number。

Then we want to run lesson， which will lesson on the port。 and then we want to run， except in a loop。

So except well wait for an incoming connection。 And when it happens。It's going to return。

A filescriptor for the new connection。Well have one for the listening。Yeah。

Connection or listening soet。And then we will get one for each connection， and then we will。

Dump this over to our callback function。 So like the handler in this case。Alright。

 so you need to do these things one at a time。So， we're gonna set our。Red equal to socket。

 This is going to be an Internet socket。Soock streamre， which is T P。 and the last argument。

 which is just0。And。Yeah。嗯。If this rest is less than 0。嗯。In that case， we want a return。An error。

Let's say that。 error is。嗯嗯。Faied to initialize。So。And we need to create this return arrow macro。

Let's do it now。So what does this return error need to do， Well， it's going to return。

And it needs to return a server。Pointer， so we need to allocate an object like that。And。

And we need to。Somehow tell it that its。It has failed。

So our server object needs to have some kind of。Let's see。Let's say， we have。An end a。Status。

And we also need to have。An error message。So， let's say。Let's do it as an array。The error message。

Like this。And the status。We can make this。 What's it called。An enum。So let's， never mind。

 Let's define it up here。Or。Let's do it here。 So we need to have an enum。

 We can make it an an anonymous enum like this。We are we gonna have a。Aristtus。Okay。Okay， that。

Those two。Right。😔，So， we actually only need to have。Well， we only need to have one bit。Okay。

 so we need to create the。Macro4。The errors。return。Arrror is going to take an X。

 which is our error message。And let's do the。While。😔，I mean， the do trick。

HSo let's see here we need to allocate one of these objects。SoWe need to have a server。

 Let's call this serve。Serve like this。Serve is going to be equal to。Well， we need to。

Calculate how big this thing is going to be。 So let's say in 16。Size。

Where the size is going to be equal to the。Size of astruct S。Server。Plus。

 the length of the error message。So。16。Version of。String length。哦。like this。Plus1。Right。

The service is going to be。We need to do this。The serve is going to be equal to。The server。

And we will allocate。Size bys。We can assert that。 We have a serve。Let's clean it out。So。

 we can use mapm set。We want to set。Our serve structure。Fill it with cereals， and。

Size number of zero。so。I wantan to take this serve object。嗯色。The status to。Aris status。

And then we need to cope with the error message。So we can do a mem copy。

We need to copy it as a sh into our serve dot。A message。We want to copy from the Charr of X。

Maybe we should。Save this。 we create one variable for。The length does well。So， we can set。Do this。

Let's say length is equal to this。So we can reuse it here。As an interview。And that's pretty much it。

So now we just return this。Serve。Object。And we don't wanna loop。 So we will do while。False。来瘦。

I think this is going to work。Cllay it should。All right。So at this point， we have a soft guest。

 now we need to。Initialize。A structure。 The sock structure。So it needs。

 so it knows what I P address and port， etc cetera， to bind to。So we're gonna set socks in。

Family to A F I， we're gonna set。W。2。😔，And we need to turn this into network back order so we can run H to S。

On the integer version of our port。嗯。We will have a sin address。Source address。Which is going to be。

In address， any。Which is a constant， which listens to every I P address。

And I we to bind them together。 So let's set our return variable。To bind。

And we will provide the integer version of our socket file descriptor。We will。Cast into stroke。So。

Addres。We provide our so。Pointer。We reference。And。Then， we have this length。Ting。

Never really remember how to do this， but I think。We need to do something like you just size of。是啊。

Sogar。Maybe， something like this。Allright， and this should return 0。So， if our return。And。

 by the way。If。We do get a socket。 We need to set our S。Equal to the in 32 version of。I will return。

Because we are overr it here。So if our return is not 0。That case， we want to close down our。S。

I we want to return。An error of。Yeah。Unable to bind。W。Okay。

 so the next thing is to listen to the socket。What are the arguments， I think。

I need to check the manual。

![](img/bff847de8a22c1f9128f39b7d601c680_9.png)

Man。To listen。Okay， so the F D and the back。

![](img/bff847de8a22c1f9128f39b7d601c680_11.png)

Un successuccess，0 is returned， al right。So the soet filescriptor as an integer。And then the backlog。

 how， how many。Incoming， unhandled。呃。Souckckets。Do we wna。Q。

And this is not really necessary in our case， since we'll be accepting all of them。

 So let's just say 10 or。And if this returns。Positive。We want to close down our socket。Return。😔。

An error。Unable to。Listen。Or， do something。Alright， so the only thing left is to accept。

The connections， which we need to do inside of a loop。So let's create another set of those things。

 So we need to have a socket file descriptor for the incoming connection。

 and we need to have a socket structure as well。So， let's call this the。嗯。S clay。For client。

And this is the。Cide。Right， so at this point， we wna run。By the way， we wna。Let's see here。

We don't want accept the connections。At this point， by the way。

 because we w to run this lesson for that。So in this， at this point。

 we just want to return one of our structures。Alright。So we're gonna have a server。嗯。Serve。

Then in 16 for the。Sizeize。Size is going to be equal to。Size of。Stred S。嗯。Server。

And we don't need to add any extra here for the error message， since there is no error。

And if there will be an error at later points， then we can。Create a new structure。Alright。

So let's allocate for this。 So our serve is going to be equal to。Mello。Size。And we can， actually。Sir。

Or no。Let's do some。 Yes， by the way， let's do serve， serve。

Because if we get a a memory error at this point。All bes are off。Okay， to do do。

Then we won memet this thing。0。Sense。And let's just fill in the fields。 So we need to have an。

We need to have an FD。The status。In an error message。And their message should be nothing。

So we can take the serve， and it。File thescriptor， which is going to be our S。And the status。

It's going to be。mm。By the way， let's save the port as well。The status is going to be okay status。

And then we'll return serve。Like so。Okay， so now we have this。Figure it out。So what else do we need。

 We need to have this O and this error。诶。Is our method。So， let's create those two functions。

We can make this private。嗯。So we're gonna have a private。

I think we can make them private since we are going have。Since we're gonna use them as methods。

 I don't think we need to publish them。It'll。We'll know when we try it。Alright， so let's call this。

 I don't know。We need a bullion。ok，放松。😔，W。And we need a private。Avoid， no， not void a private。Q。

A message function。Or what did we call。We just call it error。 That's good。 So error。Function。嚟首。😔。

And in order to keep track of our server object， we need to have a global variable for that。

I don't really like global variables， but。It's not really possible。你了你爱朵喂。😔，So。See here。

This is going to be a server object。It's call it。Gbo。Serve。It needs to be public。

And we need to have some kind of initialization function。Let's say we have a private void。Star。

And it needs to be an in it function， which we need to define。And that's some kind of a tribute。

Think it's like this。If I remember correctly。So this function is going to run when this library is loaded or initialized。

So public， no。pri。一年。Stars。And the only thing we're going to do here is setting our global serve。To。

Sir。0。And when we run our TP server， we want to make sure that this is not occupied。😔。

So if we have a global serve， which is not 0。We will return an error。Something like this。

And before we return here。Let's set our global serve to serve。Okay， so。

Now that we have a global variable， we can。Create these two functions。

Our O function are our error function， because it wouldn't be possible to find the server objects otherwise。

So， private。嗯。Por bull， by the way， if you gonna use bos， we need to include something， include S。

体力布。😔，Does age。And。If we want to use a cert， we also need to include some stuff。

We need a third dot 8。We need。Our number dot age。And we need to define you。Source。Like song。So。

 private to。Something， what did we call this O function。let's first check。We have a global serve。

 so if we don't。We will return false。Otherwise， we wanna return based on the。Global serve。Status。

So if this is equal to O status。That case， we want to return true。Otherwise， false。

This is the whole function。Then we need something for the error message。The private。乔儿。A message。

Fengg。Same here。 if we don't have a global serve。We can return。String of。TCP server， not initialized。

If。Our global serve。Has a status。Which is not equal to。Our status。Think we call it that。Yes。

So it's not equal to Aristotus。In that case， we wan to return no error。And otherwise。Let's return。

stringing version of。Global serve。L message。Simple inner。😔，Now we just need to link。

Those as methods to this。Right here。So。We will have a function pointer。怎播。😔，ok。Avoid。

Think this is it。Then we need to have a chor。呃。哦4。So two function pointers。

 which we need to set when we initialize this。So our Ser dot okay is going to be our okay function。

 or it' going to be the address of our O function。Which reminds me we need to do the same here。

The address of our handler。And our。A function is going to be the error function。Okay。So， almost done。

What we have left is our li and function。So， private。For convenience， let。

Let's just return a regular integer。So， private inn。Listen function。Boyid。can。Private inn。

Listen function。So what are we going to do here， First， we need to check that we have a global serve。

 If we don't， we need to。Return narrow。Let's just do this。So actually， we don't need to have those。

Extra。Variables here， since we will do this in another function。So， let's create。AndIn。32 S。

Signed in dress。Struck。So。Addres。So。I think we need to have some。



![](img/bff847de8a22c1f9128f39b7d601c680_13.png)

Thing for the size。 Let's check the accept。H， so let's see here。 address length。We can leave this0。

 as is specified here。But if we do， we will not get any information。About the。

I P address and stuff of the connecting thing。Okay。



![](img/bff847de8a22c1f9128f39b7d601c680_15.png)

![](img/bff847de8a22c1f9128f39b7d601c680_16.png)

Solenty。

![](img/bff847de8a22c1f9128f39b7d601c680_18.png)

是。L tea。So， let's have a sockland。Well just let。Let's call it land。And。

Let's also have a socklanee star。Len pointer。It's not strictly necessary， but let's do it。

It's also check that we don't have an error condition。So， else if。Global serve。都。No， global serve。

Status。If this is equal to an error status。Well also return minus-1。Otherwise。

 we should be able to start accepting connections。So first of all。

 we need to fork into the background。And exit。The main process。So let's see here， if 4。Is 0。

So what Fork does is it。Splits this running process into 2。And if for return 0， we are dealing with。

The main。A thread。So。I wanna exit the main thread。So all the code down here is the child process。

 which is in the background。And that's the point we want to run the server in the background。

But we do also want to fork。As soon as we have accepted a connection。

So let's set our length to the size of a struck so address。In。

AndOur land pointer should point at our land。Then we want to loo。Forever。

We gonna set our return to accept。We need to provide the。Global serve。Fscriptor。As an integer。

We need to provide。Struck sock address。So。And we need to provide our land pointer。

And if our rat is equal to 0， everything is okay。Otherwise， it's an error。So， if。If rest is positive。

That means that this accepting。Of the connection failed。And if it fails。

It's very possible that the next will fail as well。 And this will be a endless loop， which will go。

Over and over， very fast。So I usually like to do a sleep here。For， let's say， two seconds。And。

AndThen we can try again。Accepting the next connection。Something like this。ok 嗯。Otherwise， we。This。

 the connection will be established at this point。 So what we want to do now is we want to create。

One of these connections。😔，nectionね。Objects。And pass it to our handling function， our handler。

So let's create an in 16 size。 We also need to have what did we call these objects。😔，Connections。

a connection con。So。😔，Our size is equal to the size of astruct S connection。

Then we will allocate for it。And if this fails。In that case， we want to close this connection。See。



![](img/bff847de8a22c1f9128f39b7d601c680_20.png)

What's the return value of acceptance， I think it made some error here。



![](img/bff847de8a22c1f9128f39b7d601c680_22.png)

Yeah， it returns a file descriptor on error-1。Good luck。 called that。

So if R is less than 0 then we want to do this。 Otherwise， we want to set our S。一。2。😔，Really。Right。

 so let's close down this connection。Let's sleep for two seconds， and let's continue。

No wait second turn。Yeah， let's continue。The size is not going to change。

 So let's put it outside of the loop。Otherwise， we can clean this out with mapets。

And now we just need to fill it out。So we have an FD。 We have a host， and we have a port。

So the F D is our S。The host is。Let's see here。We have something called I address for turning。

An IP address as a string into。Any integer type。 And now we need to do the other way around。



![](img/bff847de8a22c1f9128f39b7d601c680_24.png)

What's that called。Let's see here。Iest N T， O， A。Ex that is。Deprecate。

So what are we gonna use instead。Is a dis thing struck。电影。Strt in the address。

Why do they need to remove all the good functions。

![](img/bff847de8a22c1f9128f39b7d601c680_26.png)

Maybe we can use it anyway。So， I and the OA。

![](img/bff847de8a22c1f9128f39b7d601c680_28.png)

嗯。T I， and we provide。Struck it。

![](img/bff847de8a22c1f9128f39b7d601c680_30.png)

In address。Ds。 I think that is。安尔。So。Do。Sin address。And then we have the port。

 the local port number for this connection。Guess we can just run an Hged to S on it again。So。😔，新ore。

😔，Something like this。And now we want to pass this。To our handle function。So。Let's see。Okay。

We provide the handler。At this point， when we run the TTP server function。

So we need to store that inside of our object。So。Here we need to have a function pointer。Handler。

Or what did we call it connect。Call back。Yeah。Its calleded CB。Let's not forget to。Said that。

Here we have a CB。Before we return。So， I will serve C。It's going to be C。Okay。

 so now we have it saved。 Now we can use it inside of our lesson function。At first， we want to fork。

 So we want to have one process per。connectionnection。So， if we are still in the。Main thread。

 so to speak， we wanna go to the next one。And we want to clean up。A little bit， first。This con。

 we don't need to save。 So con is equal to， I mean。Free。Yeah，Let's say。If called。Free code。嗯。

And since there are two different processes， it doesn't matter that were free this thing。

We can still use it in our， our， in our other process。

 because all of this stuff is copied automatically。So the code we put。After this， if statement。

 will run in the child process of this。呃。Well， of this connection。So now we just want to return。Our。

Handler。Let's see。We wanna run con dot， connect back。And what arguments do we have。4。😔。

Our connect bag。The connection， okay。Went around this without word calm。

And this doesn't return anything， no。Exit 0， like so。

So when we have handled the connection with our handler， we will exit this child process。

But the main process will continue to accept。Connections in the background。

And this should not be reached by。Even in this case， let's just do exit 0。Returned 0。Alright。Okay。

 I think this is going to work。We also need to have this list function here。So， that is。Ying。Listen。

Great。Which we also need to set。Our initialization function。So， Sir。

Lis equal to the address of listen。Alright。Hm。So the only thing， really。That is left is our。Well。

 it's not much left。Actually。That we need to create some。Temporary。Handler functions。So。

 we know how to。Use this。Maybe we can have a method on the connection for sending and receiving data。

Yeah， why not。So， let's say。You have an in。Receive。Which is going to take。Let's see here。

We can actually create a global variable for this， too， which will only be used inside of the。

Process because well only have one。Thank you for that。I mean， one。one connection。Per handler。So。

 let's say we have a public。Connection。Global con。嚟首。😔，So， before we。Call the call back。

You need to set those things。Global con。Sak go to call。Let's also set these methods。 So we'll have a。

Sound。Which is equal to a send function。And receive。Shes equal to a receive。Fun。

The only thing we need to provide is char buffer。And the number of bytes。To receive。She is。也是这个例子。

And same with the send。Like so。So， we will have a。receiveceive function。

And those will be very simple functions。手链。Receive function。We have your。See， we have only。Sace。

And we need to check that we have a global con。So if we don't have a global con。Or we don't have a C。

Or we have0。Size。If any of this happens， we will just return an error like this。Otherwise。

We will return。Yeah。The Re system call。And we want to read from the global con。Yeah。

FD or what do we call。The file is script。FD。😔，And we copy it over。Yes。So we're w to read from that。

As an integer。And then we just provide the sea and the size。So。And same with the send function。

But in this case， we want to return right。Take so。Very simple。 Very simple， indeed。So。

 let's just create some。Simple handler。有。Let's say， we。Have a buffer。So sure but。I don't know，1，28。

The first we。Yeah。We send something。Let's see。Welcome to server。



![](img/bff847de8a22c1f9128f39b7d601c680_32.png)

![](img/bff847de8a22c1f9128f39b7d601c680_33.png)

19 characters。And then we read something。So， we receive。Into our buffer。On27。And let's just pray。

Received。The like this。So this is how the program we using our library。Is going to use。It will just。

Just the sound function。2 arguments like this。And the receive function。To early。Very simple。Okay。

 that's pretty much it。Now， we only need to fix any potential errors。



![](img/bff847de8a22c1f9128f39b7d601c680_35.png)

Un type name， connection at line 14。

![](img/bff847de8a22c1f9128f39b7d601c680_37.png)

Okayay。😔，I guess we need to。Move this down or not。Here， maybe。



![](img/bff847de8a22c1f9128f39b7d601c680_39.png)

Warning sea tours at tribute directive ignored， O case， maybe it's not sea tours。



![](img/bff847de8a22c1f9128f39b7d601c680_41.png)

sDouble check。嗯。Let's see here。 JCC function。Tribute。Constructor， deor。



![](img/bff847de8a22c1f9128f39b7d601c680_43.png)

It's exactly what I was looking for。Okay。We need to type it all in。



![](img/bff847de8a22c1f9128f39b7d601c680_45.png)

So， it's not sea tours。Consstruct。

![](img/bff847de8a22c1f9128f39b7d601c680_47.png)

![](img/bff847de8a22c1f9128f39b7d601c680_48.png)

A。Private in。Vid star。m。Forgot to。Create this， so。Private void handler。



![](img/bff847de8a22c1f9128f39b7d601c680_50.png)

It's a lot of errors， by the way， but probably a lot of them will be solved in one。Pen stroke。

So let's see， storage size of so。Is not known， right。 We need to include a couple of things。

So we need。 Let's start。喂。Soets。

![](img/bff847de8a22c1f9128f39b7d601c680_52.png)

![](img/bff847de8a22c1f9128f39b7d601c680_53.png)

And then， we did。Bind。😔，And， listen。Then accept。What else。We did do aged on X。



![](img/bff847de8a22c1f9128f39b7d601c680_55.png)

![](img/bff847de8a22c1f9128f39b7d601c680_56.png)

And we did Eina can tea away。

![](img/bff847de8a22c1f9128f39b7d601c680_58.png)

![](img/bff847de8a22c1f9128f39b7d601c680_59.png)

The I。address。

![](img/bff847de8a22c1f9128f39b7d601c680_61.png)

Indeed。😔，Stringing of age， for me said。What about。Maybe this is。



![](img/bff847de8a22c1f9128f39b7d601c680_63.png)

All we need。

![](img/bff847de8a22c1f9128f39b7d601c680_65.png)

Florida。The age。do do do right。 This should be a pointer。Same here。



![](img/bff847de8a22c1f9128f39b7d601c680_67.png)

Asignment to char void from a compatible pointer type char star star void。

So either we should drop the。A percent， or we need to。



![](img/bff847de8a22c1f9128f39b7d601c680_69.png)

Add another star for this one。is66。

![](img/bff847de8a22c1f9128f39b7d601c680_71.png)

![](img/bff847de8a22c1f9128f39b7d601c680_72.png)

![](img/bff847de8a22c1f9128f39b7d601c680_73.png)

Let's see if this solves it。

![](img/bff847de8a22c1f9128f39b7d601c680_75.png)

No。So， Sir， I。ItsThis one。So maybe we need a star here。



![](img/bff847de8a22c1f9128f39b7d601c680_77.png)

![](img/bff847de8a22c1f9128f39b7d601c680_78.png)

Yep， it fixed it。 No， we just need to。Do the same for the rest of the。



![](img/bff847de8a22c1f9128f39b7d601c680_80.png)

Something like this。

![](img/bff847de8a22c1f9128f39b7d601c680_82.png)

Yeah。The violence did work this time。

![](img/bff847de8a22c1f9128f39b7d601c680_84.png)

![](img/bff847de8a22c1f9128f39b7d601c680_85.png)

Where。

![](img/bff847de8a22c1f9128f39b7d601c680_87.png)

![](img/bff847de8a22c1f9128f39b7d601c680_88.png)

![](img/bff847de8a22c1f9128f39b7d601c680_89.png)

![](img/bff847de8a22c1f9128f39b7d601c680_90.png)

![](img/bff847de8a22c1f9128f39b7d601c680_91.png)

![](img/bff847de8a22c1f9128f39b7d601c680_92.png)

， listen。

![](img/bff847de8a22c1f9128f39b7d601c680_94.png)

Mhm。

![](img/bff847de8a22c1f9128f39b7d601c680_96.png)

Instar void。Ying。Star in in。

![](img/bff847de8a22c1f9128f39b7d601c680_98.png)

哦。Listen is able to listen。This should be， listen。放弃。😔，Right。



![](img/bff847de8a22c1f9128f39b7d601c680_100.png)

Okay。Assignment to expression with array ray type。

![](img/bff847de8a22c1f9128f39b7d601c680_102.png)

conhot。I。Actually， a cha array。 So we need to do string copy there。Yer。

We need to put it inside a conhouset。We're gonna copy it from。This。50。😔。



![](img/bff847de8a22c1f9128f39b7d601c680_104.png)

嗯嗯。Okayay。😔，十侈。😔，In store star。In star。

![](img/bff847de8a22c1f9128f39b7d601c680_106.png)

![](img/bff847de8a22c1f9128f39b7d601c680_107.png)

![](img/bff847de8a22c1f9128f39b7d601c680_108.png)

Connection has no member named C，1，41。CB。😔，Because the connect back function is not the word inside of that。

Lobo。That's the one。

![](img/bff847de8a22c1f9128f39b7d601c680_110.png)

![](img/bff847de8a22c1f9128f39b7d601c680_111.png)

This is just type of。Pise。

![](img/bff847de8a22c1f9128f39b7d601c680_113.png)

。

![](img/bff847de8a22c1f9128f39b7d601c680_115.png)

This is a point。

![](img/bff847de8a22c1f9128f39b7d601c680_117.png)

And now it' compd。 I w to。Get rid of this an， annoying warning stuff。The handler declared static。

never defined。

![](img/bff847de8a22c1f9128f39b7d601c680_119.png)

Right， this should be handle prime。

![](img/bff847de8a22c1f9128f39b7d601c680_121.png)

Okay， so now only all of these are just redundant。Private。



![](img/bff847de8a22c1f9128f39b7d601c680_123.png)

So that。😔，Remove those。In our make file。I will just add a flag。So I paste this in。

And after the double， I will add no。E dash， no dash。



![](img/bff847de8a22c1f9128f39b7d601c680_125.png)

![](img/bff847de8a22c1f9128f39b7d601c680_126.png)

O。Like this。

![](img/bff847de8a22c1f9128f39b7d601c680_128.png)

And now， ladies and gentlemen， I think everything will compile。Yeahay。All right。

 let's try this thing out， shall we？Listening to Port 85，85。It did not fork into the background。

 though。Let's see what happens if we connect to this thing。Welcome to server。

And what if you type something food。Received food and some stuff。With all this。He serve。😔。



![](img/bff847de8a22c1f9128f39b7d601c680_130.png)

Need to。Clean that thing out first。 So let's see here。嗯。So it's inside of our handler。

Before we receive， we should。Clean this。Bffer。let's do， mom'm said。8。0，1，20。



![](img/bff847de8a22c1f9128f39b7d601c680_132.png)

But why didn't it fork properly into the background。



![](img/bff847de8a22c1f9128f39b7d601c680_134.png)

Let'See here。TCP server。Should be inside of the listen function。So we do the exc。Okay。

 we wait for the No。Here for。This should be the other way around， like this。

Because we want to exit the main process。Which means that。

We probably did it the wrong way here as well， right。Because the fork is 0。Then， we are the child。

This is the right。Wed that it worked anyway。

![](img/bff847de8a22c1f9128f39b7d601c680_136.png)

Well， well。Okay， now it's forked into the background。Welcome to Server。F。Received fo Newland。



![](img/bff847de8a22c1f9128f39b7d601c680_138.png)

So， it works。Pretty eyes。 Pretty eyes。But we want the connection to be closed when the handler function returns。

 right。嗯。So， let's see here。Inside of our。Listen function。So we called the call back。😔，And then。

 we exit。Maybe we should close。Dist thing first。C。The S。



![](img/bff847de8a22c1f9128f39b7d601c680_140.png)

嚟首。😔，呃。That's weird。嗯。The address is in use。 But why did it crash。



![](img/bff847de8a22c1f9128f39b7d601c680_142.png)

It should print an error message， right。次。😔，What do we do here。This bind failed。

Which means we close down this thing and we return this error。What does the return error macro do。

Is it something wrong with this construct？We haven't。嗯。We haven't set the function the methods。

 That's probably why。So when we have allocated this thing and cleaned it out。We wantan to say。

The serve。Okay， equal to the O function。And we wan do the same for the error。行。



![](img/bff847de8a22c1f9128f39b7d601c680_144.png)

Okay， now it looks better。That still were。服。

![](img/bff847de8a22c1f9128f39b7d601c680_146.png)

Well， it works， but it does not。Close the connection。I will return from this handler。We close S。

And then we X。So we close it and we exit it， but it's still。Openvis。



![](img/bff847de8a22c1f9128f39b7d601c680_148.png)

![](img/bff847de8a22c1f9128f39b7d601c680_149.png)

![](img/bff847de8a22c1f9128f39b7d601c680_150.png)

So， let's see here。嗯。So we read the fo。Prited。We close。We exit。But it's still open here。 Why is that。



![](img/bff847de8a22c1f9128f39b7d601c680_152.png)

Maybe we need to close it in on both sides。That's right。Where do we fall。Listen function。Down here。

So let's close the S before we do anything else。

![](img/bff847de8a22c1f9128f39b7d601c680_154.png)

![](img/bff847de8a22c1f9128f39b7d601c680_155.png)

![](img/bff847de8a22c1f9128f39b7d601c680_156.png)

Okay， now it works。Okay， we have successfully created a library。So I hope you like this episode。

 If so， please like and subscribe。And。

![](img/bff847de8a22c1f9128f39b7d601c680_158.png)

Thanks for watching。 Thanks for today。

![](img/bff847de8a22c1f9128f39b7d601c680_160.png)
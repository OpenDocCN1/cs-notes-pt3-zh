# LLVM开发者大会-US-｜-2025-Llvm-Developers-Meeting-p40-P39_错失的虚拟化机会调查--BV1ejr5BAEja_p40-

![](img/1df01e87a777c52eca81bedff636048f_0.png)

So I'm going to talk about an ongoing investigation of some of the missed opportunities in individualization。

 It's a work in progress。 So basically I can talk about the current status。So。Okay。

 it was supposed to have be animated。呃呃。So first， let me briefly review what whole program differentialization。

Das in LBM。 So when we have a class with。Viual function。We will have some global values in the code。

 so there is type info。 it's the first one in the rectangle。For our purpose。

 we only need to know that it exists。 we don't need the details。 there is alsoty in for name。

 which is a global string， which is each of the these appear once per class。

 one we have one of them for each class。And then we have virtual table。 Vi table has。

And some some type metada annotations， type met data can be used。To reconstruct the hierarchy。

But we don't need to know more about it for the purpose of this stock。 What is important for us is。

That the pointers that we have to virtual functions in the V table。

 the offset of these pointers in the table is important。诶。

And this only shows a single inheritance for that's enough for our purpose。 So on the bottom left。

we have a small hierarchy， three klasses， each of them has its own implementation of fo。

And you can see at the same offset， if you look at the visual tables of these three glasses at the same offset。

 you will see the pointer to the corresponding implementation for function4。And。

And what WPD does is to check for every pair of type info VT offset where for every pair。

 we basically check all compatible V table so that type info is basically points us to a class。

 we look at the hierarchy under that class， if we see only a single implementation。

 we say it can be deualized otherwise it cannot， it cannot。So when we have a。We shall call。And。

So in the middle of the picture。诶。You see， that's a typical pattern that we see when we have a virtual call site in the code。

 so consider the hierarchy on the left side。On the bottom left， we have three klasses。

 all of them basically use the same implementation as that was defined in class A。So， if we have。

An object of chaos。C， and then this object makes a call to function full。诶。

We have that type checked load intrinsic。诶。Right before the virtual call。 Now。

 if you look at into that intrinsic， there are two important parameters。

 One is the offset in the virtual table。And the other one is typing for name。

And the important thing here is that the type in for name that we see。

Is pointing to the class that implements the function that is used。 So in this case， it's class A。

 It's not class C。So we look at class A， we look at top of。We look under class A in the hierarchy。

Which you can see on the left side at the bottom。And we will see a single implementation。

And this can be virtualized on the right on the hierarchy on the right side， if we look at class A。

 we will see multiple。Implementations are under A， and it cannot be deviualized。So with this review。

 we can see the first group of opportunities that we miss。If we have a hierarchy like the one on the。

This is slide。So。If you look at the entire hierarchy。

 there are two different implementations of food。 One is by A at the root of hierarchy，1 is by B。Now。

 if we look at Ks C， it inherits from A， it doesn't have its own implementation。Now， if we look at。

 if we make a function called， we look at C4 on the left side。And we look at the table， the。

The intrinsic right before the virtual call， the metadata that we see in the intrinsic is pointing to class A。

 and then we look under class A， we see more than one implementation and we cannot devisualize it。

But if you would expect that the object that makes the colleagues of type C and。

If you take this example， it's a leaf class， there is no alternative implementation under sea。

 so it should be devized。But given the current algorithm， we cannot do it。Now you may ask， okay。

 Ken is it correct to rely on the data type of C， we have not really investigated what happens if we want to fix this and how frequent this appears。

 how important it is。But this particular question of whether we can rely on data type of C。

 that's something already the visualization ass。That data type of objects are reliable。And。

It's actually not difficult to write a program that has a typecast C style typecast between two classes。

And。Without without the virtualization， their behavior will be different。

But this gives us another idea， which is basically， okay， how we can。How we can。

 if we keep track of the。Data type casts somehow can we individualize more。

And one particular class give us surprisingly large number of devization。That is described here。

 This code is from myQl。So。At the top red rectangle， we have declared variable privileges。

 it's an object of class Jsonri， Jsonarri is a leaf class， it doesn't have any children。

It has a parent， which is Jason Dom。Then in the middle triangle。

 we take the address of this object and pass it to a function called at Colog。I。

 and if you look at the。诶。Signature of at Clogne， you will see we it takes a Jason Dom。

 Jason Dom is a parent of Jason Ar。Now， if this function is in line， if ad colonne is in line。Then。

 and we can keep track of。The the pointer address us of privileges。

 and we can kind of go back to the declarationlareration and prove that this object was constructed here and is off type。

Jasonari， then we can do the visualization。Now， there is。

 there are legality questions that needs to be answered。 It's work in progress。 But at this point。

 the first is step is to okay， estimate how useful this can be。

And its one issue is that there is a phase ordering problem here， because。

You want theization to expose in linening opportunities。

 But here inlinning inlinning exposes divization opportunities。

 So there is a little bit of problem here。So what we did as a first attempt， a very quick experiment。

We。We basically。Added our extra round of the virtualualization after inlinning in LTO。

 some opportunities are exposed by inlinning in compilers。

 but then LTO in learninging exposes more and then we added another inlinning after that and in the table you can see some results from some workloads particularly MySQL has a very large number of deviualization。

The number of inside parentheses comes from the the exact kind of。Opportunity that I talked about。

 the performance gate seems small， but it's notworthy that for something like MyQL。

 it's very difficult to get even half a percent from the compiler is not easy。Yeah。

 I think the time is over。 Thank you very much。Okay。


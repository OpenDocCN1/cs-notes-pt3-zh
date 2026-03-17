# 【全集】伊利诺伊大学 数据结构与算法 中英字幕 1080P p08 Lecture 8 - 模板与链式内存 -BV1t9FHzdEYL_p8-

So welcome back， we're going to finish off。Talking first about method dispatch and inheritance right so rather than watching me handwrite this。



![](img/f88f79e49a671bd7e40512bec0dad7c5_1.png)

I've made a slide， so here is what we did before for method dispatch right， these are the rules。

I've slightly rewarded them this time。 But when you are trying to determine what code to run。

 when the the system is trying to determine what code to run， it will run the method as follows。

 It'll look at the type。 The method is called on right。 So it is something like C dot。Get length。

It's going to look at the type of C。Check type。And then it's going to see if that method is in that type if it is。

It's going to check if it has the virtual keyword。 If it does， it'll then say。

 am I really a more specific type， And we saw that with using a reference。

 So we had a cube reference that referred to a rubikk's cube rather than just the base cube。

And then it'll go。Back to two， and it'll now use the type that it actually is。 It'll check there。

And finally， if it no finds no method， it goes to the base type。



![](img/f88f79e49a671bd7e40512bec0dad7c5_3.png)

So from this， we had this chunk of code and we got down to here。Ri。



![](img/f88f79e49a671bd7e40512bec0dad7c5_5.png)

So we got down to here and we had said this was going to print cube， random cube。And cube。

And in the case of two， it was going to print cube。诶。And then let's see what Ruik。

And then here it was going to print cube。

![](img/f88f79e49a671bd7e40512bec0dad7c5_7.png)

Because here。There was no virtual。

![](img/f88f79e49a671bd7e40512bec0dad7c5_9.png)

So right， since there was no virtual， we used the method of the type。Did you see what you need there？

Okay， I'm going to go on and I need to go to the other slide。

 you can grab the slides on the website and use it in another window also。



![](img/f88f79e49a671bd7e40512bec0dad7c5_11.png)

I would recommend that would make it easier。 So in three， we do cube。In the case of Rubik。

 we look at Rubik and it says， oh， there is no cube type。Um， it's just a brighter day。

It's a little bit sunny today instead of quite so so。And here we get Rubik。



![](img/f88f79e49a671bd7e40512bec0dad7c5_13.png)

And here is where virtual comes into play， right， that this virtual here in three oh no in three doesn't matter oops。



![](img/f88f79e49a671bd7e40512bec0dad7c5_15.png)

I confused which one I was doing。We get cube here because there is no rubric one called3。And cube。

And with four， we get cube。Rubik。And here we get rubk。Because how does that work， Let's see。

 So we look， we see that we are a cube。 It says virtual。



![](img/f88f79e49a671bd7e40512bec0dad7c5_17.png)

Um， so it says looks here， if it says virtual in Rubik's cube。

 actually it turns out that the way virtual works is if the base class at the very base says virtual。

 they all get it， people will often write virtual here。To make their life clearer。But if。

If virtual is set is marked on the method in the base class。

 all of the versions of that method from all inherited all derived classes will also be marked virtual。

 but that's actually a very good question。

![](img/f88f79e49a671bd7e40512bec0dad7c5_19.png)

So okay， so this is where we got to。Right？Here we just used rule1 here。And in these cases。

 we are all using， we start。Or rule two， here we see the difference between。Virtual and not。

 So this is virtual， not virtual。So then we have one last thing。 And now I need to tell you that。



![](img/f88f79e49a671bd7e40512bec0dad7c5_21.png)

If this chunk of code。Was here。Some of this wouldn't have compiled。

What does virtual mean virtual means that you want to use the most specific type， I mean， in a sense。

 what it literally means is if the type is virtual， check the runtime type。😡。



![](img/f88f79e49a671bd7e40512bec0dad7c5_23.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_24.png)

Okay。

![](img/f88f79e49a671bd7e40512bec0dad7c5_26.png)

So， but now we see something funny me。And if I actually compiled this code。This would not compile。

Oops。And why？So down here， we have virtual print 5。



![](img/f88f79e49a671bd7e40512bec0dad7c5_28.png)

Parin equals 0。

![](img/f88f79e49a671bd7e40512bec0dad7c5_30.png)

What the is that。Well， this is pure virtual。A pure virtual function。Fengsun。I。If。

Or I should say method。Since it doesn't make sense to have a pure virtual function。I he。Method。That。

Is declared。Yd。Equal to0 and virtual。嗯看。MP intro will be running tonight。



![](img/f88f79e49a671bd7e40512bec0dad7c5_32.png)

And I apologize for the delay。So what does this syntax mean？😡，So this is a pure virtual function。

Are of pure virtual method。What does it mean， Well， I'm going to digress just a teeny bit。

 because I think this is really cool。And。It can help you understand what is going on in a slightly deeper level。

 perhaps。That。I mean， it's just syntax that says this function must exist。But doesn't。So。

But why did they choose this？Well。It turns out that function names。

 functions are really just pointers。They are really just this name is really going to be the。Address。

Of。Code。To run function。Okay。That's it。 That's true of all of them。 right。

 that name is just the name that is just going to be in the compiler。

 the address of where that code is。And here， what are we saying， We're saying that's zero。

And zeros kind of null， right？So we're saying that this function has no address。

 so clearly you can't call it。Right。

![](img/f88f79e49a671bd7e40512bec0dad7c5_34.png)

So why do we have a pure virtual function？😡，If we have a pure virtual function， then。If。A class。

Contains。A pure。Virrtual。Method。Then。Yit。Is a pure virtual。Class。And。You。Cannot。Create。Instances。

So what does that mean， Yeah， it's an abstract based class。Also called。Cold。Abstract。TheB class。

It's the same thing。 So why do we create some methods with virtuals and others out Well， in here。

 we're trying to just show the behaviors。

![](img/f88f79e49a671bd7e40512bec0dad7c5_36.png)

It's a design decision。And here， what we're saying is that if we create this。

 what we're saying is any class that inherits from this， any class that。

Is derived from this base class in order to really create one， we'll have to implement this function。



![](img/f88f79e49a671bd7e40512bec0dad7c5_38.png)

So since C is a abstract。Has a pure virtual function and has a pure virtual class or an abstract base class。

 we cannot do this。It cannot be compiled。

![](img/f88f79e49a671bd7e40512bec0dad7c5_40.png)

But Ruk is O。 Why？ Well， Rubik has overloaded。The function， so Rubik has implemented print5。😡。



![](img/f88f79e49a671bd7e40512bec0dad7c5_42.png)

So Ruk is fine， and it will print rubbik。And in this case， is it okay？

It's very similar to what you would do as an interface in Java， but。The rules end up different。

The details aren't going to matter to us if you start doing lots of this， you can dig into the rules。

 but yeah it produces a very similar result to what you get from an interface in Java。

 but it's a little bit more complicated because for example， your pure your abstract base class。



![](img/f88f79e49a671bd7e40512bec0dad7c5_44.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_45.png)

嗯。Also can have data in it。

![](img/f88f79e49a671bd7e40512bec0dad7c5_47.png)

Well， because the compiler would look at this and say。This is not a valid function。

And so this is an abstract past class。 And here you have asked me to create a cube C。



![](img/f88f79e49a671bd7e40512bec0dad7c5_49.png)

I don't know how to create a cubeB C because I don't know where to put this function。So。

 I can't do that。Because if you call C dot print 5， what' will happen。I don't know。

 I don't know what to do here， so I will not create this class。😡。



![](img/f88f79e49a671bd7e40512bec0dad7c5_51.png)

Because it has a pure virtual function in it， so it is a pure virtual class or an abstract base class。



![](img/f88f79e49a671bd7e40512bec0dad7c5_53.png)

And hence， cannot be instanted。Can you still create a reference？ Yes。

 this is fine because I haven't created a C。I have created a reference to a C。

And I refer to it to a thing that actually exists， so this is fine and we will print Ruk。



![](img/f88f79e49a671bd7e40512bec0dad7c5_55.png)

What is print 5 equals 0 actually do， It makes the class。 It says this function does not exist。

 but must exist。If print 5 is not overloaded in Rubik's cube。

 then it would not compile either and it。Would also be a abstract base class。

So it says this function， the equals zero says。You must have the defining it says you must have this function。

 and this says， and it doesn't exist here。Its instructions saying anything of this type must have this function。

If it doesn't have the equals zero， then it's just a function。



![](img/f88f79e49a671bd7e40512bec0dad7c5_57.png)

Row 5 column 3 is being we have a reference to a cube that points to a rubic's cube。

It can have defined methods and undefined virtual， pure virtual methods， it can also have data in it。

😡，So you could say。Well， every， I'm going to store a bunch of data。That everyone's going to get。

 but everyone that inherits from me has to define this behavior。

And it has to define this behavior because it's legal to write this right。

 this is a legal line to write。

![](img/f88f79e49a671bd7e40512bec0dad7c5_59.png)

The equal0 says that this function is pure virtual and。



![](img/f88f79e49a671bd7e40512bec0dad7c5_61.png)

This rule says that if a class contains a pure virtual function。

 then it is a pure virtual class and you cannot create one of them。



![](img/f88f79e49a671bd7e40512bec0dad7c5_63.png)

Well， if you just wrote print 5， then this is exactly the same as print 4， right。Yep。

 if a class inherits from a pure virtual class and does not implement the pure virtual functions in that class。

 it would also be pure virtual。To define an interface that everybody must use。

There is no way to define an abstract class without having at least one pure virtual method。

 Because why would it be abstract。What is the difference between cube， colon， colon and defining。

 I don't understand what you're asking。Pure virtual is doing the same sort of thing that abstract is doing。

 Well， because any place I have a type cube， such as I do here， I can write the line C dot print 5。



![](img/f88f79e49a671bd7e40512bec0dad7c5_65.png)

Right， so if I have。All if I have a interface， I have a function that takes a reference to a cube。😡。

Or it takes a pointer to a cube。That then I always know I can call the functions that are defined for that class。

That those functions are pure virtual means that somebody else has to overload it。

But I can now write code that any time I have a cube pointer， I can do print 5。

 and if you decide to implement your thing， you will have to have implemented the print 5 method。😡。

So I can write code safely。Once you have one pure virtual function。

 all functions of the class become abstract， no， the class becomes abstract。

The functions are either defined or not。Right。So you can create functions that have to be overloaded in the base class。

 You don't intend to use the function in。It only makes sense for a function to be virtual。Deo。

That is correct。 That's the whole thing that happens with an abstract class is you cannot create an instance。

 which is why this column would not compile， because you're trying to create a C。

Can an abstract class inherit from an non abstract class sure。Can you do cube colon， colon。

 print 5 equals 0， No， that doesn't mean anything。 The equals0 can only go in the header file。



![](img/f88f79e49a671bd7e40512bec0dad7c5_67.png)

This， in this case， we have not this is the only piece in the header file there would be in the header file exactly the same syntax。

 but here I needed to show the code。

![](img/f88f79e49a671bd7e40512bec0dad7c5_69.png)

All the code would would compile。 So right， the code for these functions would compile。

 but you cannot。

![](img/f88f79e49a671bd7e40512bec0dad7c5_71.png)

That with line 18， the rest of the code would compile， right， This isn't the dot H file。

 This is the CPP。 Yeah， so in the dot H file。I probably should have made a separate window。Okay。

We're not going to deal with this a whole lot， but it's something you should see。That help。



![](img/f88f79e49a671bd7e40512bec0dad7c5_73.png)

Okay。So that's what I've got。

![](img/f88f79e49a671bd7e40512bec0dad7c5_75.png)

U， it would be an error to define print 5 in cubebe。cppP after having defined it as pure virtual。

I don't know what the compile error would be because I'd never done it。A method is on a class。

 a function is just a function。A method is a function that acts on a class。

A function is just sitting around。 If you're coming from Java， you've never seen functions before。

 you've only seen method。Methods are specifically functions that act on a class， but right。

 we've seen things like PA。Pow takes。You know。A function takes arguments。And returns to value。

 but it doesn't。Act on anything。 A method is a function that always acts on a class。



![](img/f88f79e49a671bd7e40512bec0dad7c5_77.png)

Okay。So now we're going to start a teeny bit of data structures。A break from pure C plus plus。

A teeny bit of data structures leaks in before we do the last bit of C++。

 which admittedly is my very favorite bit of C++。So what we're going to talk now about is list。So。

Let's think about what we're going to have is the ADT or。The abstract。Data。Type。

And the abstract data type is the theoretician's description of the interface。4。Ei。Data type。So what？

Do you think is the interface we would have？What things can we do on list？

Tell me something you think we should be able to do to a list。Add like add to the list。 Yeah。

 so I I'm going to use insert。In west。We've got remove， I like remove， oh。

 we've got a bunch of stuff， so I like remove， remove。From。Wist。Okay。U。We've got search， Okay。

 there's a bunch of these that are really cool。But a bunch of these are like fancy things we want here is the basic things we can do to list。

 What's the minimum set of things， I mean， your super cool list sounds great to me with mergege。

 and I I saw sort up there。 I'm not sure I need bogo sort， but， you know， iterate seems interesting。

Leng lengthength is right on the edge。So here's the thing。Lots of these are cool。

 we want the minimum set of stuff， so we clearly need to be able to put things in the list and we think lists should have things removed。

Um。I'm going to say that。I almost like length。But here's a different thing。

 I'm going to say we're not going to have length。 Leth is a fancy list。 It's nice to have one。But。

But I think we need to get stuff， so get。Data。From list。We。Okay。

Fold filter and map coming from a functional language。 I like it， but we don't get that。Okay。

 get data from L。There's one。 a lot of people wanted。Length or size。Butm。How about what is it？

Instead of size， what is a minimal way to think about size？What could I ask？Is the list。Empty， yeah。

 empty is。Check。Empty。Okay。And there's one more which I don't think you're going to think of。

What is the one other thing we need。Oh we could， that's a really nice fancy list replace。

 that seems like a cool thing I can replace， though by removing and inserting iterators seem cool。

 but that seems like a fancy list to me。The constructor。We need a way to create one。No matter what。

So the constructor calling it the constructor is a little bit。I。Specific。

 but we need the idea that we can create an empty list。So， create。Empty list。不す。

That if I have these five functions， these five behaviors。

I claim this is all of the behaviors that I need to define from a theoretical point of view。😡。

From an implementation point of view， we get a lot more details like operator equals。

 but equals has a clear meaning， from a theoretical point of view， I know what it does。

Why check empty because how do I find the size of a list if I have insert， remove and check empty。

 what could I do？😡，I could write a loop where I check if it's empty， Otherwise。

 I remove something from it and put it on another list and keep doing that。

 And I find out how big it is。 And now I know the size， and I put it back in。

 It's terribly inefficient。But it is the minimum behavior。And this is going to be at front。And。Front。

With these， I can now do everything。That I need for a list。It's not the most efficient set。

We certainly can imagine other things， I love this idea of a list that can sort itself。

 I love an iterator sort of that I or perhaps the square brackets。

 there are many other things we might want， but this is our minimum set of behaviors for a list。

That if my data structure can do all of these things。Then it's a list， right？So， okay。

What stuff do we put in our list。What things might we put in the list？Groceies， I like objects。

Numbers， so we're going to put groceries。So like some lettuce。let's draw an apple。

 I can draw an apple better than lettuce， and it is a really pretty terrible apple。

 and it's not terrible。Here's my like teabone steak。Oh。Jr of peanut butter。Et cetera， groceries。

 we have integers will' have like four。2，2，5。I don't know。Credit card information。Professors。あ。

Cities will have Shim of Aurora。Not going to put my social Chicago。Et cetera， okay。

Good attempt at trolling there。But so okay， we can put all these things in list。So。Here's the thing。

How。When you write the code for this。Do any of these lists behave differently。

Because of what's in them。So if I write the code。😡，For the list， right。

 that implements this interface。The code should do the same thing， right？はい。Right。

 so let's let's talk for a moment about。Yeah， we're just changing the type in the container。

 but it's kind of a black box from the point of view of list if we have a list that sorts itself。

 it gets more complicated。But if we just have a list。Right， if this is ints。And strings。

And I implemented the code for this， right？The code would be exactly the same， except for。

 in one case， every place I had integer， I would be erasing the integer and writing string， right。

Otherwise， it's exactly the same code。So。Clearly， what we do is we write the code once and cut and paste。

And then edit， right that that that's good software engineering is based on the cut and paste method。

We've all heard that， right，So。Everybody has already been going on and pointing it。

 but what C++ does。Is templates。What are templates。 Templates are amazing。 Tlates are。Recipes。4 code。

They tell the compiler how to write code for us。And then use that code。They have types。As variables。

So。You write the code and say here is this variable and every time you see it。

 you're going to start it out and you're going to fill in whatever type they told you to。😡，Okay。

And they are， but what's really cool and why I love them。

 because I'm a high performance kind of person that I I did most of my work on making code run very fast。

Is that they are compile time。So when the compiler runs。😡，It does all of this work。It。

Can then optimize this code because it's actually working on the code。Wenyou。Use， instead。

Objects and object polymorphism。Which is powerful and a useful tool。

 It can't optimize because it doesn't know what's happening。Yeah。

 Valgr is an amazing tool that makes you realize how things can be painful。

I've been thinking about how they introduce it better because we give you a bunch of really horrible code and use it but。

If you write good code， it's not as painful， but so。What are templates。

 so let's try and look at a template。So。Om。Here is some code， and I want this to be templated。

 I want to write something that will do maximum， but'll work with both integers and floats and other things。

 So how do we write this， We are going to write in a header file， or in。In a。

 this should be an H P P file。 We're going to write this code， and we're going to write。pname。

And much like in C+ plus。We are introducing a variable here。 It is type name T。

So what we have said is we've modified the code below us。 So this code block。Is now templated。

And it is templated over the variable T， which is a type。And when we use it。

 we're going to have to give it a type。And it says it is going to return the maximum。Of a or B。

So let's try and do this。 So if we want to do。Maximum。Int。So I'm now invoking this function。

 and Im giving it an argument for its templated code of an integer， and it's going to take。3 and 5。

Well， what it will have done。Is when the compiler saw this。

 it's going to go look for the template code。And it's going to fill it out。 It's going to say endt。

Maximum。Paren int。A comma int。Bi。And result。Result。Equals a greater than B。This gibberish。

Collin return result。Okay。Vectctor is， in fact， if you go look through that code。

 if you look in vector， if you find the header file， it's just templated code。In fact。

 almost all the C library is just this。Is there a way to restrict a template type easily or do we rely on documentation。

 no。It is not under the template namespace template is a key word that it says this code is templated。

It's just under the template line you don't enclose it in brackets。Yeah， so template type name T。

They're working on features to make templates better， and there's been a lot of fighting about it。

But yeah， the thing that templates needs， it turns out is a type name type system for templates。

 I agree with you。And this is。A feature that has been coming real soon now for a long time。

But so right， this is what this code would do。 And then later。

 if I did the same thing with three points with floats， it would work。

You either template the entire thing or not， but I mean， right？Could I change this， I could。

Not everything inside the code needs to be templated， right， You can have types as well。

This is a recipe that the compiler can use， right， that if I look at this code here。The compiler。

 when it sees this。When it sees the instantiation， when it sees you try to use a template。

It will automatically use the code on the left。Can we do anything other than type name in T name T。

 It turns out you can， but you probably never should。There is also something called class。

Doesn't matter。 Just use type name all the time。 What's the difference between the left and the right hand side。

 So there's this weird syntax。 There's two other things going on here。So this says。

This is the question mark operator。And it says。Evaluate。There are three parts。

 so it is a question mark。B colon C， right？Turernary operator or the question mark operator。

 and it says。If。A。Is true。V。B else。Xi。How do you figure out if it's true， Well。

 it's going to figure it out the way you do any other expression。The template。

 the code on the So it's the ternary operator。 It sometimes helps。 I basically never use it。Um， so。

Is there a reason just to show templating and how it can be used？

So is there a difference between the code on the left and the code on the right。

 the code on the left is the code you wrote。The code on the right was generated by the compiler automatically at compile time and then compiled by itself。

😡，Why do we use this instead of if else？Because people think it looks cool in a very small number of cases。

 it can make。Complicated things， a little bit more compact。

I don't use it often because I think it usually makes code harder to read。But sometimes it can help。

 There's no particular advantage。But so that's templating。So for several functions。

 do we write templating will apply to the next function or to the next class。

Shouldn't result be a boolean type， No， we decided it was a type T。 You could instead of written。

 we could write a different function bo。And return that。 And that would be fine。

So anything can be compared if the greater than operator was overloaded。What does HPP stand for。

 that's a very good question。So。Template code is special。It's kind of。Header code。

 because it needs to be seen everywhere it's used。And it's kind of code code。

There's actually like 500， but a lot of people will watch the recording。



![](img/f88f79e49a671bd7e40512bec0dad7c5_79.png)

Maybe even 600。 but so here is how we write template code。

 We still want to preserve this idea of the interface and the implementation。So if we look at this。

 we can say here， we're going to now make a list that we're going to template。

That's literally how it started as a raper for sea。But， this is not。Okay。

 so I've now declared the entire list。To be templated。Okay。

Which is going to make this list be templated over T。

 And now what we're going to do here in this class is。Because in order because these are not code。

 but recipes， we don't want to compile the HPP， we want to make it available so that when anybody uses a list。

😡，They can compile the code themselves。Okay。Why is the included at the bottom because the code has to come after the interface？

That here is the then here I'm going to do something like。Let's see。Ru。And we'll have here。

 we'll have bo。Is empty。Wu。L。Is empty。If。There we go。Yeah， I should have used an underscore。

I've gotten good about that when typing but it's a pain， so there you go。Okay。

So we'll talk about this more and we'll show some examples of going through this。So okay。

 let's talk about it。What don't you get？Do we have to input include list。hlist。hpp no。

 but it's fairly common to do so and it'll be safe because of pragma once？

Where are we using the template in this case， Well， then we'll have our say。Ti。Pointer。Dao。

That is going to store our list。Will there be a list dot CPP no？😡，Um， why is list。

hpp at the bottom because whenever you use a list？You need， this is the list do H。

And then list that HPP。 So just like we saw in code， we would do list that H。To do。嗯。The interface。

And。Something else to do the implementation。 In this case， we call it an HP PP。

 and it is the recipe for the implementation。 So everybody that wants to use it needs the recipe。

 so they have to have it。 and the way they get it is from the include。😡，How is it different？Concept。

Conceptually， the difference is this is the thing we are going to include when we use it。

 and this is the thing that will get pulled in。Is H and HPP a real thing or just an example。

 It is one of the standard ways to do this。 You could stick all of this code in the dot H file。😡。

If we name it list。cP， will it still behave the same？The problem is if you name it list。

cppP and there is a problem here。Your tools will probably try to compile that code。😡。

Right and this code can't be compiled。Cute。Compile。It's not code。It's recipes for code。Right。

 so this is the header for the template。 This is the interfa。

 We're doing exactly the same separation。 And again， you could in many cases。

 have put them all in one file anyways。If I put it at the top， it will if I put this here。

When the compiler gets to this， it's going to say。What's this list T thing you're talking about。

 I've never heard of a list T。 You haven't told me about it。 Here is where I've defined my class。

 So until I have declared my class， I can't define it。😡，Right。

 here is the the description of the recipe。 Here is the。Actual recipe。

 What is the advantage of having it down or not， It won't compile if I put it at the top。

Because the compiler will get to this and say， I've never heard of this thing。



![](img/f88f79e49a671bd7e40512bec0dad7c5_81.png)

Where would I define T， Well， just like we saw here， right， here's where I invoke it。



![](img/f88f79e49a671bd7e40512bec0dad7c5_83.png)

So in we'll put， pretend that this is another thing。 So here we'll have the。DotcP。

And I will have what is the advantage of the template， Well。

 I only go to write one list instead of a list for integers and a list for floating points and a list for pointers to floating points and a list for pointers to cubes once。

 So then when I use it， I'm going to have list。Yt。Wist。Of impts。And I have just。Declared in Maine。

So a variable list of events that is。A list of inks。And that's exactly how I do it。

So the type is a list templated over ins。 And then when the compiler does this， it's going to go， oh。

 I need one of these things in every place in the code here that it sees T。 It's going to put in it。

Templates are great。I'll stick around and talk more， but I'm going to stop recording at this point。



![](img/f88f79e49a671bd7e40512bec0dad7c5_85.png)
# 使用-Python-和-LLVM-创建编程语言-p03-P03-Episode-3---Compiler-Foundation--BV1hn5RztEt8_p3-

Welcome back to the programming language series where we're going to build a statically typed and Gt compiled language using nothing but Python and L O VM light。

 Today， we're going to work on our compiler class and get that fully set up to handle our arithmetic code generation。

 Let's create a new file。

![](img/8aad44f1fb37348e563d0dabf579ace9_1.png)

![](img/8aad44f1fb37348e563d0dabf579ace9_2.png)

![](img/8aad44f1fb37348e563d0dabf579ace9_3.png)

Make that our compiler at pi。Now， in this compiler， we're gonna need a few imports。

 But for before we can do any of that， we need to install Lovium light。

 So this is part of the reason why I。Pushed for miniconda at the beginning of this series。

 because all we willll need to do is a command Conda， install L V M light。Now。

 if it's not really working in the visual studio terminal。

 you may need to go to your search bar and Windows and type in Ananaconda。

 There should be a little command prompt that you can open up and navigate to this directory and activate the environment and install this。

 So we'll conint Ol of M light here。 And now that it's done， we're ready to get on with our imports。

So from L L VM light， import I R。It's going to be the main object that we use today。

In this compiler class。 and we need to import everything from our abstract syntax tree file， as well。

So Im just gonna copy and paste this。 You could take it from the parser as well。

 Everything in here is matching with the parser besides this note type right here。

 We just need to add that。 So we'll get on with the compiler class。Class compiler。

 the constructor method。 But do have a few things set up in here。



![](img/8aad44f1fb37348e563d0dabf579ace9_5.png)

We're gonna have a。Type map。Which is gonna be a dictionary。



![](img/8aad44f1fb37348e563d0dabf579ace9_7.png)

Key is a string， and the value will be an I R type。 So an L L VM type。

The only two things we are interested in right now is the integer type。So IR dot int type。

And this will be a 32 B integer。And then we'll have the float type。Which is an IR dot float type。

Next thing we're gonna need is the module。 This is gonna be the main module， the main。Block。

 not block， but the main container for all of our code that we're generating。So the self dot module。

Type IR module。This I R dot module will' name this module。 Main。

 You can name it pretty much whatever。The main is what I am going with。And then we'll need a builder。

 says self dot builder。IR dot IR builder。And then we'll call that function as well。

 Next thing is going to be the main method of our compiler class， which is just going to be called。

Compile。And this is gonna take in a node。 And this is what is gonna run recursively。

To walk down the abstract syntax tree。 I's gonna go from the expression statement， go in。

To the expression statement function， it's going compile in here。 It's going visit the infi。

 It's going visit another infi。 Then it's going visit an integer and resolve that value。 So in here。

 self that compile，In this compile method， we're going to use a match case statement So match no dot type。

 This is where our function comes into play。First case will implement is node type dot program。

And this is just gonna。Visit the program。Should a function to visit the program node。

We'll pass in the node。 Now， down here， we'll add another region block for visit methods。

So we're just gonna implement this visit program method。Defisit program self could take it a node。

 and that node is going be a program node。So what we're gonna need is the。First off。

 for our language right now， we're not gonna。 some languages need to have a main method。 So in C。

 you have the in to main method。It's just the absolute execution starting point for the language。

 Right now， we are going to fake it。Just similar to how a lot of other languages do。

 We're going to create a main function and then put everything in our test file。

Into that main function， as if it was already there without us writing it。Later on。

 when we implement a little more， we're actually， going I have to type the main method our fun in our language。

But for now， this will do。So the first thing was need the function name。

Wheres going to name this function， the main function。But remember what you name this。

 because we'll need it in the main do pi file to actually call this later on。Need a parameter types。

List， which is a list of Ia type。So what what are the parameter types for this function。

 It's going to be completely empty for right now。

![](img/8aad44f1fb37348e563d0dabf579ace9_9.png)

And the return type is an IR type。

![](img/8aad44f1fb37348e563d0dabf579ace9_11.png)

And we'll set that to our tight map in the integer type。

So we're gonna return an integer from our main function。

So we need the function type in the actual function。Block as well。So the F N T wise。

 this gonna be our function type。Is IR that function type。We have to put in our return type， first。

And then we're going to put in all of our parameter types。

And then we'll have our actual function for our IR function。First is our module。 So self dot module。

 Then we'll put in our function type。And then we'll put in our name equals function name。

I name that funk main。 I need to name that funk name。There we go。Now。

 we need to define the functions block。 So where is all of this code going go in to the function。

So name it block equals funk dot append basic block。And we'll name that block。The funk name。

Underscore entry， then we need to set the current builder。For this function。

 So this will be scopeed to whatever's in this function。So， IR builder。

And we'll set put the block into the builder。 Now， the main portion where we're going to start being recursive with our compile function is。



![](img/8aad44f1fb37348e563d0dabf579ace9_13.png)

Here with our for loops。 So four statement in no dot statements。

We're going to compile that statement。And at the end of this， we're gonna set our return value。

 just gonna be a constant variable。An IR constant。And this is where our self dot type map will be。

 It'll be a type of integer， and we'll make it。The nicest number in the West。

So self dot builder dot R。 So this is the return instruction。

So we want to return from whatever function this builder is on。

 So we're going to generate that return instruction and we'll just return this return value。

 We can move on to the beautiful expression statements。 So in our compile match function。



![](img/8aad44f1fb37348e563d0dabf579ace9_15.png)

![](img/8aad44f1fb37348e563d0dabf579ace9_16.png)

We're going to add a comment for statements。 So every statement visitor method will go here。case。

 node type dot expression statement。

![](img/8aad44f1fb37348e563d0dabf579ace9_18.png)

We'll do a self visit。Expression。Statement。It pass on the note。



![](img/8aad44f1fb37348e563d0dabf579ace9_20.png)

And we'll go ahead while we're here， just do the expressions block。And then we'll do a case。

 node type， dot infi expression。

![](img/8aad44f1fb37348e563d0dabf579ace9_22.png)

Self dot underscore， underscore， visit。Infi expression。M Brag noted there。

First thing we'll do is expression statement， though。

 and we're going to have a internal region block as well in here。So region， this will be statements。

This is all our visit methods， for statements。A defaf visit expression statement。Taken a node。

 which is of the type expression statement。Donon't turn anything。

And all this will do is just for now， compile。

![](img/8aad44f1fb37348e563d0dabf579ace9_24.png)

The no dot expression。 last visit method we'll need to implement is our。And fix expression。

 So we'll make another region block for that， for these expressions。So， de。Visit in expression， self。

No is， of course， the infi。Noone。We'll take the operator。Out of this。Noode we'll take the left。 Now。

 this is where we're gonna use。 we're gonna have to implement another helper function to resolve a value from a node。

So this function will return the value and the type。And then we call it resolve value。

Take in the node dot left node。And then we'll do the same for the right。It'sRight tight。

 self dot resolve value。And then we node dot right node。

 So we will go ahead and implement the resolve value real quick before we go to the rest of the functions。



![](img/8aad44f1fb37348e563d0dabf579ace9_26.png)

We'll go outside of this final end region and make a new region。Helper methods。And region。

This is a really important function Re value。 This is where。

Everything is going to originate for doing our math， for resolving those integers， floats， strings。

 arrays， everything。So that'll take in an expression。Notode， and then a value。Type。

 and this will be use。It'll at a later date。 But we'll just go ahead and put it in here now。

This will return a tuple of an IR value object and an IR type object。



![](img/8aad44f1fb37348e563d0dabf579ace9_28.png)

We'll have a match statement。

![](img/8aad44f1fb37348e563d0dabf579ace9_30.png)

Based on the nodes type。First case is node typed integer literal。We'll go in just， this is。

Purely for intelligenceence。Equals node。Value。Type。

We'll do use capital T because lowercase is reserved by Python。First is gonna be the node dot value。

And then we'll do a little bit of。1 liner， if statements here。Tight map。It'll be an integer type。

 if value type。Is none。Else， value type。So this will always be known until we implement using this value type。



![](img/8aad44f1fb37348e563d0dabf579ace9_32.png)

Where we're just gonna set it up now。IR dot constant will just generate it in return a new IR constant with the type of type and the value of whatever value that is。

And then the second part of the tuple will be the type。Same thing for the float literal。

 You can just copy， paste this， and。Copy paste the integer part。

 but change everything to just say float。

![](img/8aad44f1fb37348e563d0dabf579ace9_34.png)

Now， the last part is the expression values。So there are cases where an expression will go into this resolve value function。

 The only what we're going to care about right now is the infi expression。

 and that we' just call our infi expression function as well。



![](img/8aad44f1fb37348e563d0dabf579ace9_36.png)

![](img/8aad44f1fb37348e563d0dabf579ace9_37.png)

So back up to the in， we'll finish this out。

![](img/8aad44f1fb37348e563d0dabf579ace9_39.png)

Said the value equal to none。We'll set the type equal to none。



![](img/8aad44f1fb37348e563d0dabf579ace9_41.png)

Now， if is instance。This is a built in function in Python。

 just to check if one object is the same class or type of as another object。

So we'll take the right type。If that right type is an integer type。And。



![](img/8aad44f1fb37348e563d0dabf579ace9_43.png)

Is instance。Left type is an integer type。

![](img/8aad44f1fb37348e563d0dabf579ace9_45.png)

We want to take this type equals self dot type map。 This will be an integer。

And then we're gonna match again on the operator。

![](img/8aad44f1fb37348e563d0dabf579ace9_47.png)

Depending on which operator we use， we're gonna。Amit a different instruction。 So plus。Value。

Equals self dot builder， dot addd。Left value。

![](img/8aad44f1fb37348e563d0dabf579ace9_49.png)

Right value。Well add another for our minus sign。Value equal self dot builder dot sub。Left value。



![](img/8aad44f1fb37348e563d0dabf579ace9_51.png)

Right value。Then I'll copy and paste these other two here。



![](img/8aad44f1fb37348e563d0dabf579ace9_53.png)

So this is for multiply just the M UL function and then slash for divide S div。Now。

 these functions for are different for floats。So we'll implement that a little bit later。

 Just want to get the integers out so we can see this generated I R， and then we'll finish it。

 So we'll， we'll。

![](img/8aad44f1fb37348e563d0dabf579ace9_55.png)

Hang off on the modulus in the pow operators until the next episode。

 But this should get us through for right now。

![](img/8aad44f1fb37348e563d0dabf579ace9_57.png)

And then， we will return the value。And type。From this function now， from right here。

 we can actually go to the main dot pi file。

![](img/8aad44f1fb37348e563d0dabf579ace9_59.png)

![](img/8aad44f1fb37348e563d0dabf579ace9_60.png)

From compiler， import compiler。

![](img/8aad44f1fb37348e563d0dabf579ace9_62.png)

And there's a few weird imports that we're going have to do So from LL VM light。

 we're going to import IR。

![](img/8aad44f1fb37348e563d0dabf579ace9_64.png)

From Er import LVM light dot binding。

![](img/8aad44f1fb37348e563d0dabf579ace9_66.png)

As L L V M。And then we're going to have to use the C types。Majuo。😔。



![](img/8aad44f1fb37348e563d0dabf579ace9_68.png)

See types。Import sea funk type。

![](img/8aad44f1fb37348e563d0dabf579ace9_70.png)

When we take a C integer in a C float。I don't。 We will not use these yet， but when we're executing。

 we will use these C types。 It moving down， We're gonna grab this program and take it out of here。



![](img/8aad44f1fb37348e563d0dabf579ace9_72.png)

We to put it above this。We're in a check。If the length of the。Pser dot errors。It's greaterer than 0。

We'll just print them to the screen。P dot errors。And print the error。

And then I'll just exit out of this。Program with a code of one for now and not。嗯。Next thing。

 we're gonna set up our compiler class。Get an instance of that。We're gonna。Hit the compile function。

No dot program or node equals program。Now， these are output steps for now。



![](img/8aad44f1fb37348e563d0dabf579ace9_74.png)

We're going take the module。Which is an IR module。the C dot module which is our compiler。

We're going to set the triple。 So this is our basically our target architecture。

This is just gonna get the default triple from whatever operating system you're using。

And I'll show you where this is in the IR。We'll go up。 We'll add a compiler。Piler debug flag。

Thats true。We'll sent this to false， for now。AndThen we'll come down here and we'll check that。

 So if compiler debug。We're just gonna with open。Debug slash I R dot L L then as F。

 we're going doing F dot right。

![](img/8aad44f1fb37348e563d0dabf579ace9_76.png)

And we're just going to stringify the module that we got up here。Alright。

 so this should all that we need。 We need to， I guess we can create a compiler dot line。

 You can still use one of these if you want， but we'll implement 5 plus 5 with this semicolon。



![](img/8aad44f1fb37348e563d0dabf579ace9_78.png)

And we will run。Python， main dot pi and see if we can do it now。All right。 So IR do LL has been made。

So this is the LL VM。

![](img/8aad44f1fb37348e563d0dabf579ace9_80.png)

Intermediate representation code。So we have our module。 This is where we named our module main。

 This is the target triple。 I'm on a。64 B PC， that's a Windows。So that is my target triple。

 just automatically grabbed that This data layout we， we。

 we can take care of later doesn't really matter for right now。

This is the main function that we created from scratch inside of the code and that we just injected the rest of ours。

是 this是。Is where we return in I 32， which is an int，32 B。The name of that function is main。

The first block in that function is the main entry block。This is where we add。

You can take the compiler right here。So this is where we add。

 The first instruction is our addd instruction。 It's an integer， add 5 plus 5。

 and that will go into this variable。And then I guess we forgot to set the compiler。Test。

 so I think it just used the parser。 yet did。 alright。So， use the parser。Where's my IR。Alright。Now。

 we're here。So it uses the parser file。 So that's okay。 It's a little better。

So the the next thing is this 03。 It multiplies the result of this  point。2， which is 5 plus 5。

And then it multiplies that by 10。And then that's where we can get whatever this is。

 that's the value is stored here。 We don't have a way to see it yet。But and then we have our return。

 nice number， Beaut number。Down here。 and that is the I R code。So this gets a lot more complicated。

 a lot more complex， but there's no need to get that far into it yet。 We will take this step by step。

But that's the end of episode 3。 In the next episode， we're going implement the rest of our。

Arithmetic operators。 So thank you for watching。 Discord is in the description。

 if you have any suggestions。Or any features you wan to see added to this。

Please leave that in the comment section as well。 I will see you guys in the next episode。



![](img/8aad44f1fb37348e563d0dabf579ace9_82.png)
# 使用-Python-和-LLVM-创建编程语言-p02-P02-Episode-2---Pratt-Parser--BV1hn5RztEt8_p2-

Welcome back to the programming language series where we're going to build a statically typed and Jit compile language all using Python and LVM light。

 Last time we got the Le are situated for our arithmetic language。

 So today we're going to get the parser situated for our language and we're going to be using a technique called Prat parsing。

 I'll let you guys read more down in the description below on Prat parsing。

 But we will get right into building this out。 So the first thing we're going to do is create a test file。

So we're going to call that parser dot line。And we're just going to put 5 plus 5 in here for right now。

 So from here after we have this file created， we can get out of that。

 we won't need it for a little bit。We'll go ahead in the main dot pi file。

 change that departure parser dot line。And then we will create our parsed Pi file。And get started。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_1.png)

Few imports that we're gonna need is our Lexer。So from Lexer import Lexer， from our token。

We're gonna need。😔，Our token class and our token type class from from。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_3.png)

There we go。And then， another typing。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_5.png)

Import， this is optional， of course， but。I like it for the Inence。 We're going import collable。

Which is pretty much just like a function type。And then we're also creating another enum so from enum。

Import。F spell， genomeum and auto。 And that's all for the imports right now。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_7.png)

We're going to set up our precedentnce。Types。The pratt parser is an operator precedence parser。

 So we need to set up。Kind of how our precedences are mapped in what levels。

 Which one's the lowest and the highest。So for that type， this is going be a enum。Precience type。

We'll inherit from that Eum class。First。1 we're going to implement is P lowest。

 which is this is the lowest precedence。Absolutely。The least priority， pretty much。

We're going to go to P equals。And we're going to use that auto function that we imported。

 All this does is it just takes the next。It replaces it with the next appropriate value in this enum class。

 since we're starting with a 0。The auto functions is going have in a one。And then， P less greater。

Equals auto， that's gonna resolve the two。 And then we're using this auto function that way。

 later on。When we add different precedentnce， types or levels。The。

 we don't have to actually change everything。 So we don't have to change this to two if we add one here。

So this auto function just can help out later。Now， there's a few more。

 I'm going to save some time from having to type that out。But we have P sum product， exponent prefix。

 call an index。 Now， this is every precedence。That we should need throughout this series。

 there will be more， of course， if we have some requested features。But this should do for a while。

Next thing is going to be our precedence mapping。Pside mapping。And this is just gonna be。

A big dictionary。Keys the token type。And we're gonna call a。Not an int。

 but the precedence type as the value。So the first one we're going to implement is token type dot plus。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_9.png)

This is a plus symbol plus token。And that is， of course， gonna map to our piece some。

Value or precedence type。We're going implement every other operator that we have。

So we have minus slash asterisk， modulus and P。 We'll have a lot more in this class。

 or in this dictionary。But for right now， this ist all that we need。

 This is everything we have implemented。 So we'll go down and we'll start our parser class。

So we'll add a class parser， add a constructor in it method。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_11.png)

The only thing that this。Constructor is gonna take in is an instance of our Leer。

 and we'll set a variable self dot Leer。A type Leir equals Leir。Her not， like。The actual variable。

We're going to have an error list。 So right now， all we're going to care about air handling is just having a list of strings。

 So self thought errors。There a list the strings， and we'll just print out the errors as we generate them。

 We'll have a more。Robust error system later down the line。 But for now。

 this will do We need two variables， self current token。So whatever token the parser is currently on。

 and then we'll have a peak token。Which is whatever， whatever token is next。

 what the par is going to take on next。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_13.png)

Then we'll have two dictionaries。 We'll have a prefix。Pse。Functions， this will be a of token type。

Valuable is going to be a function to call based on the token。We'll keep that prefix functions。

 Basically are're going to handle like negative one negative。

 this little negative symbol is a prefix to one。We're going to have infi parse functions。

That'll be a token type。And a callable for the value。An in fix。

Functions are going handle like 5 plus 5。So， the operators inside。

Were in the middle of two other nodes。 So 5 and 5。 the last thing we're going to set up。

 we don't have this function yet。 but this is what we're grabbing next。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_15.png)

Is our next token function very similar to our Lexer。And this will actually call our lecture as well。

Moving into our next token function。I'm going to do some region blocks just to kind of help this。

 this file will be。Very large。In the future。So it's always going to be good to have these region blocks to segment out the code。

And all that does is you can collapse everything in this region block really easily。

 And this is its title， moving into the depth。Next， token。Have self， and we will grab none。

For the return type。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_17.png)

So we're going to take the self dot current token。 We're going to set that to our peak token。

 So the next token。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_19.png)

And then we're going basically increment this peak token to be whatever the next token is from the Lexer。

AndThat is all for the next token function。 What we're going to do is go ahead and build out all of these helper functions just to avoid us。

Having to go back and forth。Throughout the code to recreate helper functions。

And I feel like that would be a little more confusing than just getting them out of the way right now and explaining them。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_21.png)

So the next function we're going implement is our peak token。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_23.png)

Peak token is。That's gonna have a self in a token type， P T token type。This's can return a boolean。

This basically just peaks the。Checks our peak token that we have saved in the parser class and checks its type。

And see if it is equal to the one that was passed in。It self dot peak token not type。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_25.png)

Whats T T。 Next one is going be underscore underscore expect。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_27.png)

Peak。Self T T and token type。This folk， this function is going to basically expect we're gonna check'ca we're expecting this。

 the peak token to be of a certain type。 And if it's not， we're gonna throw an error。So， if。Self答案。

Undercorner score， peak token is。If the peak token is that token type， we're gonna increment。

The tokens， and we're going return true。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_29.png)

Else。We're going to throw another function we'll create in a second。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_31.png)

Peak here。With the token type and return turn false。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_33.png)

All this peak error function is going to be doing is just a helper function to append an error to our errors list。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_35.png)

So peak air will' take stealth and the token type。I won't return anything。

 It's just gonna pen to our errors。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_37.png)

F string and we'll expected next token。To be this token type。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_39.png)

Instead we got this self dot peak token dot type。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_41.png)

Instead。So I'll go ahead and just save time and paste this in here。

This is the no prefix parse function error。 We'll use this when we're checking the prefix parse functions in a later。

 later method。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_43.png)

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_44.png)

And the last two things that we have to implement， I will just copy and past these just for the sake of time。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_46.png)

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_47.png)

It's for checking our precedences。 So we have our current precedes and our peak precedence。

This just gets whatever precedence level is associated with our current token and our peak token as well。

And it will return back the lowest precedence by default if one is not implemented yet。 So allright。

 we can collapse this code block， move down， and we're gonna start off with our main execution point of the parser。

 which is going be our parse program function。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_49.png)

Self and none。Now， we will put a pass in here because there's something else we need to set up。

 We need to set up all of our classes and nodes for our A S T。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_51.png)

So we'll go ahead。Knock that out with one full swoop for just the ones that we need for this arithmetic language。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_53.png)

So we'll grab a new file， A T dot pi， only a couple imports from ABC。Import capital， ABC。

 an abstract method。 This is just， we're going to use abstract classes to help with the In。

So these are some things we need to import for that。 And we're also going to have another Eum。

 So from Eum， import Eum。First class we're going to make is the node type class。

 This is the type of A T node。This will be an enum。We're gonna have the program node。

 which is like our main root node。Of the A S T， top most level。

We're going have all our statements right here。 The only one we're going to create today is called an expression statement。

We're going to have a set for expressions。In fixed expression。Equals in fixed expression。

 and then are have two literals。We our integer literal。And then we'll have our foot literal。

And that should be all the AS T nodes we need today。 We'll start off with our parent class。

 So our node。Will inherit from ABC。So the first thing is gonna be we use the abstract method decorator。

This's gonna be the nodes type。And that will return back a node type。

And we'll just pass for now since we're in the parent method。We'll have another abstract method。

And this will be for。Turning the g or returning back the Json representation of our node。

This is purely for debugging。 There's no other reason to have this other than just being able to see our A S T in a pretty Json file。

 So I'll let it pass right there。 So we're going to add two more child classes to know。

 They're just going to serve as Ins。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_55.png)

So class statement。We'll inherit from node and just pass into of that， then class expression。

Will inherit from node as well。 Pass out of that。Allright。

 So let's get on to our first actual A T node。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_57.png)

This will be our program node。You know inherit from node。This will take an in it method。

Weon't take any variables in， but it will have a property of statements。

This is just a list of statement notess。This are just all the statements that。

Make up the entire program that we were creating。Will implement the type method。

This will just be the node type。That program。Will implement the Json method。

Sort of turn a dictionary。The one key for type， and we'll call our type。Function。

 you need to use the dot value because no type is an enum。 and we want this string value instead of。

The actual enum value。Next thing， we're going have a block for our statements。Now。

 we're going to use a little pythonic thing called list comprehension for this。

 Just going to make it easy one liner。You could。Do a four loop up here and then populate a variable into here。

feel like there's too much for using Python。 Let's roll。So in this list。

 we need to do four statement in self dot statements。

And at front of this for loop will make a dictionary。

The key will be a statement dot or type function， dot value。Is equal to statement dot。

 we'll call whatever that statement' Json value is。

 And this is going to pretty much recursively build out。The Json A S T file or the A T Json file。

 Alright， we'll move on to our statements。 So we'll make another region block statements。

We'll do and region。Class will be an expression statement。So will inherit from the statement class。

 which is inheriting from node。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_59.png)

This will have an init method。The only thing this will take in is the expression。

And then this will default to none。Self dot expression equals expression。

I guess we'll add a tight hint as well。 one not。Will'll implement the type function。No type。

 dot expression statement。And the Json function。Type key will be self not type。P value。

The expression key will be the self do expression， not Json。

 So whatever this expression node ends up being。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_61.png)

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_62.png)

We want to grab its JSO representation。Alright， we have three more nodes to implement。

 The next one is going to have its own region block for expressions。This will be the infi。Expression。

Or hear it from expression。So in this in it method。

 this is a little has a little more going on with it。 We're gonna have a left node。Which， of course。

 would be an expression。The operator， which will be a string。 And in the right node。

 is also an expression。We'll default that one to none。 So this is like the five。

5 plus 5 Left node would be this5 integer。Operator would be plus left the right node would be this5 integer。

So in this method， I'll paste this just to save a little time typing it。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_64.png)

So just setting these variables up into the class。So implement the type method。

So this would be the node type in fix。I implement the Json method。We have a type。Self dot type。

 dot value。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_66.png)

The left node。Will be the self dot， left node， dot， whatever their Json representation is。Operator。

 self dot operator。Then the right node。Self dot right now， dot Json。All right， so two more。

 I am going to just paste in here， just for。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_68.png)

Time's sake， of course。Let' have another region block coliterals。We have an energyteger literal。

 All that's taking in is an energyteger value。And。Setting up every the same way。

 Every other node is being set up。 Float is exactly the same as integer。

 except everywhere it says int。 you want to grab a float。 Now that we have this A S T fully set up。

 We'll save that file， and we can get out of that for now。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_70.png)

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_71.png)

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_72.png)

Go back to our parser file。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_74.png)

Go up to the top。And we will start importing from our A S T。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_76.png)

So I have just them segmented out to like our root。

Intelcent nodes pretty much at the top with our program。 I have。

 Im going to have all the statements on this line， all the expressions on this line。

 all the literals on this line。 There will be a lot of nodes to import。

 So I'm just going go ahead and。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_78.png)

Organize it as I can。 We're going down to parse program。Go ahead and implement this function。

So first off， we're gonna need our program node。Create an instance of that。 So while。

The self dot current token not type。Is not equal。The token type。Of end of file。

 So it's not our very end of the tokens。 We still want a parse。We're going to get a statement。

And that will bring us to our first function， parse statement。We'll implement that in a second。

 If statement is not none。We're going append this statement to。Our program nodes， statements。

And then we're gonna increment to the next token。The very end of this will return the program。Return。

 return， turn program。We'll return the program back out to Maine。

 And that's what will be sent into our compiler。 So the next two functions we're going to implement。

 we're going to put them inside another region block just to help it out。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_80.png)

State， oh my goodness。 I can't spell statement methods。 There we go。And region。First off。

 we have the deaf parse statement method。So。And this will return back a statement。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_82.png)

And then this will， as of right now， this will have a lot more in this function。 But for right now。

 with our arithmetic language， we don't really need to do anything in here。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_84.png)

So we'll just go ahead and。Paarsse down to our parse expression statement。Now， in our parse。

Expression statement function。 We'll go ahead and just copy paste that。

That's can return back an expression statement node。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_86.png)

First， we'll set a variable for our expression。So we'll call another function。

 This is the pretty much the root of the prat parser， which is the parse expression function。

 And this will take in a。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_88.png)

The precedents type will just give it the lowest。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_90.png)

To start off with because we're not exactly sure yet which precedes we should be giving。Then。

 we'll grab a。If statements， a self dot peak。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_92.png)

Token is。And I'll check for a semi con。So that if this statement is done， so in our parser。

 if we see a semicolon， that means this expression statement is done。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_94.png)

We'll just move on to the next token。And we'll build out our expression statement。

 class or As T note。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_96.png)

Our expression is equal to expression， and we'll return back the statement。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_98.png)

Now， back into the tree， we can get out of。The statement methods。We take this parse expression。

And head on down to another region。Expression methods。And region。

So we'll do a deaf parse expression self。 And this will take in a precedence。

Which is just the precedent type。有冇 go。Return back an expression from that。

So this is where we're going to use our prefix and infi functions。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_100.png)

Parse functions。 So we'll go ahead and set these up near these comments。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_102.png)

So in our prefix functions。We need to just handle integers， floats， and left parentheses。

So these are going to call another group of functions thatll parse an in literal。

 a float literal and a left parentheses， which is just a group expression。

There will be a lot more in here， but the so we need now in the same with the infi parse functions。

 We'll paste all of these in。 and this is where we'll implement all of our operators。

So every single one of these just calls this parse infi expression。

 So we can go ahead and implement these three different or four different functions。

 These two are pretty much the same。 So we'll go ahead and implement these。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_104.png)

I'll go with parse in fixed expression first。So we'll pass out of that and come back to it。

So de parin expression， be a self。And this will take in a left node， which will see。

In a minute where that comes into play。Let' sort return an expression。The in expression。

In fixed expression。Build out that class。 left node is left node。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_106.png)

And the operator is a self that current token dot literal。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_108.png)

Now we'll leave this right here becauseuse I feel like。Maybe一。

This needs to be explained a little more on how it's called。

 So we'll go back to the parse expression function。And we will implement this。

 this whole function before implementing the rest that need to be called。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_110.png)

So the first thing in prefi in the parse expression function is prefix function。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_112.png)

The type of collable， or it could be null or none。We're going to check our prefix parse functions dictionary with the Git method。

And we're just going to get the self， whatever our current tokens type is。

 We're going to get that prefix function for our whatever current token we're currently on。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_114.png)

If that prefix function is none。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_116.png)

This is where our。No prefix parse function error comes into play and will send in that current token type。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_118.png)

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_119.png)

T呢。Now we'll grab the left expression， and we'll set that to what our calling of the prefix function that we got up before。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_121.png)

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_122.png)

Now， we need a check for in operators through。If there's any in fixed functions for this。

 So while not。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_124.png)

Self dot peak。Token is。Token type dot semicolon。And the precedence value。

 So we need to use dot value because of the enum， we need to get that integer out。

Is less than the self dot peak precedence。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_126.png)

Dot value。So while all of that is true。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_128.png)

We're going to grab and see if we can get an in function out of this token。Out of the peak token。

Self dot in fixed parse functions got gi。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_130.png)

Self。peak token。t type。If the in fix function is none。We're going to return that left expression。

Go ahead increment to the next token。We'll set the left expression equal to whatever the result of these。

 of this infi function。We'll put in our left expression or our left node that we were talking about earlier。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_132.png)

In the very end of this will return back whatever the left expression ends up being。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_134.png)

So we'll go right back into our in fix functions。 since now we see where it's called from。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_136.png)

So we need to get a variable for our precedes。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_138.png)

Just to save it。 and this will be whatever our current precedence is。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_140.png)

Using our function。We increment the token。Will set the infi expressions right node。

 equal to whatever。we'll parse that。 It is equal to an expression。

 so we're going to parse the expression at whatever precedence we saved up here。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_142.png)

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_143.png)

And we'll return back the infi expression。 Now we'll move on to the grouped expression。

 So we'll grab this。 This is for our prefix functions。 So deaf parse grouped expression。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_145.png)

Takes in nothing other than self， and will turn an expression。First thing off。

 we'll go ahead and increment to the next token immediately。I'll grab the expression。

From our parse expression method。And the precedence type will be the lowest because we're not sure what we need。

If not， self dot。On this corner core， expect peak。Token type。Dot right parentheses。

this is a grouped expression。 So it's whatever。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_147.png)

Is it within two parentheses。 So if after we。Paarse that entire expression。

 If the last one is not a parentheses， That means we have a syntax error。

 So we'll just return none out of that。 The expect peak function will already append to that error。

 so we don't need to do it。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_149.png)

Here。And we can return whatever expression is out of that。 Now。

 the last two functions that we need to implement are。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_151.png)

parse in literal， and the parse float literal。So we'll make a region for these prefix methods。

And region。Now I'm going to paste these in here and just go over really quick just for the sake of time。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_153.png)

So， the integer literal。Just creates a new integer literal node。

 We try to convert this value into or we try to convert this literal into a integer。

If that doesn't work， we'll append an error and return none。 If it does work。

 we'll return back that integer literal。 and the float literal does the exact same thing。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_155.png)

Except we're using floats and instead of ins， of course。 But all right。

 I think this parser might be ready to test。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_157.png)

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_158.png)

I't see anything that I am missing。 so we will go and save this file。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_160.png)

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_161.png)

We're good at main dot pi。From parser， import parser。We we grab our from our A T。

 will import our program。And then we'll also import Json for our AST。

 and we'll set another parser debug flag。That'll be a bull that the' true。

We'll go ahead and toggle off the lectureer for now。Down here under this if statement。

 we'll get a instance of our Leir。The source equals code， nice。P for parser。 then of our parser。

 the only variable we need to put into that is our Lexor。So we'll put that Leer instance in there。

 We'll set our flag， parser debug。I have this little print statement we can add here。

I'll also add it up to the likesr， just for fun。But in here。

 we're going to grab a program node from the parser， So P dot parse program。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_163.png)

We'll open up a file。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_165.png)

Before we do that， let's grab a folder， name it debug。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_167.png)

And then we'll do debug slash AS T do JO。In right mode。



![](img/5e7a69b6b58793dc708ed1c66d1fb00a_169.png)

Nam it F。Jason dot dump。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_171.png)

Program dot Json。 That's that Json vi we。Or that Json method that we implemented each note。Put F。

 and then we'll set an indent and a four just to make it easily readable。

And then we'll just add another little print statement down here just to show that this was successful。

And now， with a little。Crossing of the fingers， I think we can check to see if this works。So， Python。

nameam that pie。Said it wrote， here we are and beautiful。Alright， so here's our program node。

 Every statement in this。File right here。So our first statement is 5 plus 5。

 so that's an expression statement。The expression is an infix expression。

And that is where left node is 5。 the operators plus and the right node is 5。So now。

 if we put these in parentheses and we。Multiply it by 10， according to Pemdas， multiplying should be。

This parentheses should be resolved first before we multiply so we can see how that looks on the A T。

So as we run this， now we have a。Expression statements where the expression is an in expression。

 The left node should be。Another infixed expression。 that is。The  five for the left node plus 5。

And then the right node of this whole expression is just the integer literal 10 with the multiply。

 So it will resolve all of this first，5 plus 5， and then it will resolve this left node's value times that right node's value。

So we have Pmdas working pretty good now。And we have our As T being built and shown in a Json file。

 Now， the next thing that we'll work on for the compiler is taking in this As T and walking the As T to generate the I R code for LL VM using LL VM light。

So we'll get that set up in the next episode， thank you for watching。

 If you want to join in our discord， the link is in the description below。

 If you have any suggestions on features or stuff that you want to see。

 please do let me know in the Discord， please do leave a comment and you will get to that。

So I will see you guys in episode 3。

![](img/5e7a69b6b58793dc708ed1c66d1fb00a_173.png)
# 使用-Python-和-LLVM-创建编程语言-p11-P11-Episode-11---Strings-+-Printf--BV1hn5RztEt8_p11-

Welcome back to the series， episode 11， where we're going to go mainly into adding a string data type。

 as well as a print function to use these strings in actually be able to see。

So this print F function will be very similar to the C implementation。 So we。

 we can use percent I in order to and extra parameters into the print F function to put the result into our string。

So this is just percent I。 So we'll add an integer here。

 So we'll call our add function that we've declared up here to add2 and 3。

 So when all this is set none， our console should say apples5 here。

So now weve got all this code ready。 and this is our goal for this episode。

 We're going to start off with our token dot pi。In token dot pi， we need add a new In token dot pi。

 we need to add a new token type for our string， string equals。Sttrirink。In our token type enum。

 And then we'll need to scroll down to our type keywords。And we're going to add two new keywords。

 one for string and one for void。 This is just something I forgot to do。



![](img/892e81ac5bbd299f3765ffe0237265c1_1.png)

In our lectureer， we're gonna do， let's go underneath the comma。

 So we'll add a new case for our double character。

![](img/892e81ac5bbd299f3765ffe0237265c1_3.png)

And this will be the same thing as everything else。 So change this token type to string。

And in order to read this string， we're going to need a new helper function to help us do that。

 So we're going to change this to underscore underscore， read， string。And more to make this。

We're gonna keep track of a position。The variable will be an integer。Self do position plus 1。

Do a wild， shrew loop。

![](img/892e81ac5bbd299f3765ffe0237265c1_5.png)

Every time this loop。Does an iteration， we're going to read a character。



![](img/892e81ac5bbd299f3765ffe0237265c1_7.png)

From our sore drink。If。The current character。Is equal to another double quotes or the current character。

It is none。We're just going to break out of this loop and say we're done。

 The strings obviously ended or there's some type of， or the file is ended。

 So there's some type of an error。

![](img/892e81ac5bbd299f3765ffe0237265c1_9.png)

So after we're out of this while loop。In our A S T。

 we're going to add a new literal to our node type enum， said the very bo。

And then we will go all the way down， and we'll add in our string literal node。

 I'm just going to paste it in for the sake of time，'cause it's very similar。

 if not exactly the same to all of our other literals。



![](img/892e81ac5bbd299f3765ffe0237265c1_11.png)

![](img/892e81ac5bbd299f3765ffe0237265c1_12.png)

![](img/892e81ac5bbd299f3765ffe0237265c1_13.png)

Except this value is just a string data type。So we'll just implement the in function。

 our type in our parser。 we can import the new node that we just。



![](img/892e81ac5bbd299f3765ffe0237265c1_15.png)

![](img/892e81ac5bbd299f3765ffe0237265c1_16.png)

We can go down to our prefix parse functions in our init method of the parser。



![](img/892e81ac5bbd299f3765ffe0237265c1_18.png)

This function will be a token type dot string， and its function will become a self dot underscoren。

 We'll add a comma， just for later。

![](img/892e81ac5bbd299f3765ffe0237265c1_20.png)

Now， the only thing we need to do in this parser is implement our parsse string literal function。



![](img/892e81ac5bbd299f3765ffe0237265c1_22.png)

So we'll scroll all the way down to our other parsllaral functions。



![](img/892e81ac5bbd299f3765ffe0237265c1_24.png)

Do deaf paring literal。So。Will turn a string literal note。



![](img/892e81ac5bbd299f3765ffe0237265c1_26.png)

And all we're going to do in this function is create a new string literal class。



![](img/892e81ac5bbd299f3765ffe0237265c1_28.png)

Value equals self dot current token dot literal。That's everything we need to do for the parser now。

 So moving on into the compiler。

![](img/892e81ac5bbd299f3765ffe0237265c1_30.png)

We're going to start it off by importing our new string literal node。



![](img/892e81ac5bbd299f3765ffe0237265c1_32.png)

We go to our tight map。 And since we added new types to our token。



![](img/892e81ac5bbd299f3765ffe0237265c1_34.png)

File， we need to add them here for how the compiler is going to see those types。

 So we're going to add string。And that's going to be an IR dot pointer type。

And that type of pointer is going to be an int8。 So an I ate or the same type as a character。



![](img/892e81ac5bbd299f3765ffe0237265c1_36.png)

Below that will add void。The IR dot。Vid type。

![](img/892e81ac5bbd299f3765ffe0237265c1_38.png)

And that's also， like I mentioned before we're going to be used later down the line。



![](img/892e81ac5bbd299f3765ffe0237265c1_40.png)

We're going to start off with our print function to kind of get that out of the way and get off the strings for right now。

 So in our initialized built ins。

![](img/892e81ac5bbd299f3765ffe0237265c1_42.png)

We're just going to add a new function here， called in print。



![](img/892e81ac5bbd299f3765ffe0237265c1_44.png)

And that's going to return an IR function。

![](img/892e81ac5bbd299f3765ffe0237265c1_46.png)

We're going to get our function type set up。 So F N TY function type is of type function type。



![](img/892e81ac5bbd299f3765ffe0237265c1_48.png)

![](img/892e81ac5bbd299f3765ffe0237265c1_49.png)

Equals IR dot function type。And we're going to start with the return type of this function。

 So it's going to be a self dot type map。 We use our integer type。



![](img/892e81ac5bbd299f3765ffe0237265c1_51.png)

The arguments of this function is going to be a string。 So I R。In type 8。So in I8。

 and we're just going to pass it in as a pointer to those。



![](img/892e81ac5bbd299f3765ffe0237265c1_53.png)

And then var A is going to be equal to true because this could have multiple parameters。

 And we want to make sure we handle them all。

![](img/892e81ac5bbd299f3765ffe0237265c1_55.png)

Now， all this function is going to do is return an IR dot function object。APas in our module。

 selflf dot module。Or pass in our function type。And then we're going pass in the name of this function。

 We want this， the compiler to register as so print F for now， now below all of this。



![](img/892e81ac5bbd299f3765ffe0237265c1_57.png)

We're gonna。

![](img/892e81ac5bbd299f3765ffe0237265c1_59.png)

Inner down， get some space。 We're going to set our environment。 Now。 We need to give our。

 let our environment know we do have a print F defined。 So self dot E And V dot defined。



![](img/892e81ac5bbd299f3765ffe0237265c1_61.png)

We're going to call the init print function for that function type。



![](img/892e81ac5bbd299f3765ffe0237265c1_63.png)

That we created in this function object。

![](img/892e81ac5bbd299f3765ffe0237265c1_65.png)

And then we're going to set the type of this。

![](img/892e81ac5bbd299f3765ffe0237265c1_67.png)

Function are pretty much the return type to an I R dot int type。

 And it's just gonna return the 32 B integer。And that should be everything we need to do for print F。



![](img/892e81ac5bbd299f3765ffe0237265c1_69.png)

This absolutely needs to be named Prif， right here。



![](img/892e81ac5bbd299f3765ffe0237265c1_71.png)

When you get to the environment part， this could be named。Yat。For all L L V M cares。

 this is on our side。 So whatever we want to define this function as is Y。

 But this print F needs to be set in the in the L L VM function object。

 because this will point directly to the C implementation of print F。



![](img/892e81ac5bbd299f3765ffe0237265c1_73.png)

![](img/892e81ac5bbd299f3765ffe0237265c1_74.png)

But just for now， I'm going to keep them both the same。The next thing we're gonna do is。

Complete our strings。So we're going to go down to our resolve value function。

 So I'm just going to search for that。 control。 Click on one of those to take me straight here。



![](img/892e81ac5bbd299f3765ffe0237265c1_76.png)

![](img/892e81ac5bbd299f3765ffe0237265c1_77.png)

Now， in the case statement underneath Boolean literal， I'm going add a new case， node type。

 dot string literal。

![](img/892e81ac5bbd299f3765ffe0237265c1_79.png)

We're just gonna set node equal to a string as a string literal type， just for the in part。



![](img/892e81ac5bbd299f3765ffe0237265c1_81.png)

We're name string tight。 We're going to take out a tuple from the self dot underscore corner score convert string method。



![](img/892e81ac5bbd299f3765ffe0237265c1_83.png)

And we're going to pass in the node dot value or the Python string that's it's referring to。



![](img/892e81ac5bbd299f3765ffe0237265c1_85.png)

And then we're just going to return back the string and the type。



![](img/892e81ac5bbd299f3765ffe0237265c1_87.png)

Now we'll implement the convert string function， so we'll do that underneath Re value。ToDeaf。

 convert string self。String is， of course， going to be a string。

 And this is going return back a tuple where the first value is in constant。



![](img/892e81ac5bbd299f3765ffe0237265c1_89.png)

And the second value will be in a array type。Now， this may。Look a little confusing。

 but it's just initializing the string in L L VM。 So it knows the location and what to refer it to。

So the first thing we're do is we're going to do string equals string dot replace。

And we're going place all of the back slash ends in the new lines with a。



![](img/892e81ac5bbd299f3765ffe0237265c1_91.png)

Back slash n back slash0。 So just like a null adding a null termmarator terminator。

 a null terminator。

![](img/892e81ac5bbd299f3765ffe0237265c1_93.png)

Create a format variable equal to the string。 And we're gonna add that null termmerator to the very end of our Python string。

 as well。

![](img/892e81ac5bbd299f3765ffe0237265c1_95.png)

We have our C format。Which is gonna be the constant version。The IR dot constant。

The type is going to be an IR dot array type。The element types in the array are gonna be。Int 8。

 So int type 8。And it's going to have a length or a count。Of the length of the format string up here。

 So how many characters are in that。And then outside of this array type， parentheses were at a comma。

And we're going to set the constant value as a byte array。



![](img/892e81ac5bbd299f3765ffe0237265c1_97.png)

And we're going to encode。

![](img/892e81ac5bbd299f3765ffe0237265c1_99.png)

FMT dot encode code。The format string as UTF 8。 So we're going make sure it's encoded that way。



![](img/892e81ac5bbd299f3765ffe0237265c1_101.png)

Now， we need to create the global variable for L LL VM for this string。

 So we'll set a variable global FMT equals I R dot global variable。The pass in our module。

Our type is next So C FMT dot type。And then we're going to set our name here， just to。

Keep everything from。Or keep things from if the strings are the same value or we don't want to have the same names for every global variable'ca they need to be unique。

 So we're gonna add a underscore underscore string， underscore。

And it will add a call to our increment counter。To grab it just a new integer。



![](img/892e81ac5bbd299f3765ffe0237265c1_103.png)

We're going to set this global FMT's linkage to be internal。



![](img/892e81ac5bbd299f3765ffe0237265c1_105.png)

We'll set the global FMT's global constant equal to true。



![](img/892e81ac5bbd299f3765ffe0237265c1_107.png)

And then we'll set the global FMTs initializer。To B our CFFMT。

 So we're going to initialize this global variable with this constant value。



![](img/892e81ac5bbd299f3765ffe0237265c1_109.png)

And finally， at the end， we'll return our global FMT， which is just our global variable reference。

And then our global F and T， the type that it is。 So it will just be a。C FM T type。

 So this constant type， which is an array of characters。

 So Iatess and the length of that string that we had up here。



![](img/892e81ac5bbd299f3765ffe0237265c1_111.png)

And we'll save that file。And strings should be。Perfectly implemented now， at a very basic level。

So we'll do our very last thing is to get our print function fully working。



![](img/892e81ac5bbd299f3765ffe0237265c1_113.png)

So we'll add a new function underneath the convert string。

 We're going set it to the name built in print def。Take。We'll have a parameterss very parameter。

 that's going to be a list of IR dot instructions。And then return type。Is an IR dot type。Now。

 I could go on for hours explaining how this code works。



![](img/892e81ac5bbd299f3765ffe0237265c1_115.png)

However， the。This is basically mapping the C。Print F function。



![](img/892e81ac5bbd299f3765ffe0237265c1_117.png)

So I'm just going to paste it in here there。Some limitations with the L L V M light library that caused this。

 So in my C sharp series， this is handled way more elegantly and able to be understood a lot easier。

 so。

![](img/892e81ac5bbd299f3765ffe0237265c1_119.png)

All we're going to do is we're going to look up our print f function from our environment。

 We're going to grab that function object in its type， but we're not really going to use its type。

 but we're going to allocate a string。With our return type here。

We're going to store that string in the compiler and that the first one is going to be our parameter 0。

 So our first parameter in our print function。 So right here。

 we're going to store that a reference or store that in memory。We have the rest of the prams here。

 which is just everything beyond。

![](img/892e81ac5bbd299f3765ffe0237265c1_121.png)

If the first one is actually a load instruction。So， if we are using a。

Variable to we're passing a variable into this print function。

We need to handle the load instruction slightly differently than just a straight up string。



![](img/892e81ac5bbd299f3765ffe0237265c1_123.png)

So we'll get that load instruction。We're to get the global variable pointer。

From that C format instruction。We're going to load the strings of value from that global variable。

We're going to bit cast it to a。Just make sure it is a。Pointer to I 8， so。A string or characters。

 And then we're going to return a call instruction to call that function with those arguments。

If we're just using a normal string， like we're going to be doing in our example。



![](img/892e81ac5bbd299f3765ffe0237265c1_125.png)

We just need to bit cast the global。 So we're gonna get that global。

 and we're going get the counter to that， as well。And we're going to make sure that type is a I 8 pointer。

And then we're going to call that function the same way。 Now， this only works with printing integers。

 I've had a lot of headaches trying to implement floats。

But the C sharp implementation is way better than L VM light。

 So that will make a whole lot more sense。 But if you do have a solution。That's pretty readable。

Make sure to join the discord and ping me on that，'cause I can update these videos。



![](img/892e81ac5bbd299f3765ffe0237265c1_127.png)

We'll do our final thing， which is a visit our call expression。

 So we'll go to our expressions region。 Let's go down till we see visit call expression。



![](img/892e81ac5bbd299f3765ffe0237265c1_129.png)

![](img/892e81ac5bbd299f3765ffe0237265c1_130.png)

We'll come down to this match statement now that we do have a name instead of just defaulting to the default case。

 we can add our print F name。

![](img/892e81ac5bbd299f3765ffe0237265c1_132.png)

We'll set the return。Value to self dot built in printf。We'll set parametersms to our as。And then。

 return type。If I can type， it will be types and the first index。In our return type。

We'll make that equal to our T mapap integer。

![](img/892e81ac5bbd299f3765ffe0237265c1_134.png)

And that should be everything we need to run this。So we'll go to our testt line file。

 We'll come down to our。

![](img/892e81ac5bbd299f3765ffe0237265c1_136.png)

Terminal， where our Python environment is activated and we' type in Python， main dot pi。And now。

 we can see apples 5。So we can change this to like 12。 And that should say 15， apples 15。

Let include or conclude our adding our strings and our printf function to our language。

 Very basic implementation。 There's a little more you could do。

 but the LovM light libraries just feels very limited and very complicated to。

Get working compared to see sharp。 So this is we'll end off here。

Make sure you join the discord if you have any questions or run into any problems。And on our Discord。

 I have the link to the full series code on our Github。

So if you want to skip ahead and look at some of the code for the later episodes。

 you can there in a little sneak peek of our next series。So thank you for watching。

 And I will see you in episode 12。

![](img/892e81ac5bbd299f3765ffe0237265c1_138.png)
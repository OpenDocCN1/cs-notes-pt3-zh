# 使用-Python-和-LLVM-创建编程语言-p12-P12-Episode-12---While-Loops--BV1hn5RztEt8_p12-

Welcome back to episode 12， where we're going to focus mainly on while loops。So。



![](img/08fdd146d5749c528b60643192da451e_1.png)

Generally， implementing any type of a loop， this will be very similar if you want to implement a dowhile loop as well。

 we won't get into that。 But there's a good challenge for you， if you want to。



![](img/08fdd146d5749c528b60643192da451e_3.png)

Test your skills。So the piece of code we're going to be compiling today is just going to be our main function。

 as always， We're going to have a variable A。 That's an integer equal to 0。While a is less than 10。

 we're going to loop and print off the value of a。And then we're going add one to a and then redo the loop。

So this should print everything from。0 to 9。And then we're just gonna return a just'cause we need to return an integer anyway。

 so might as well。So now that we have our code that we need to our goal for the episode。

 we're going start as always， in our token dot pie file。



![](img/08fdd146d5749c528b60643192da451e_5.png)

We'll scroll up to the top and in our keywords list， we're going to add while equals while。



![](img/08fdd146d5749c528b60643192da451e_7.png)

And we're going to scroll down to our keywords dictionaries。

 We're going to add our normal keyword while is map to our token type， not while。



![](img/08fdd146d5749c528b60643192da451e_9.png)

![](img/08fdd146d5749c528b60643192da451e_10.png)

And then， our alt keywords。Is going to be。We'll do we for fun。

 So we is gonna equal token type dot while。 So that will also map a while for our gen Z safe language。



![](img/08fdd146d5749c528b60643192da451e_12.png)

So now that we're done with the token dot pi， we have nothing to do in our Leer so we can move on to the next step。

 which is our AS S T dot pi。

![](img/08fdd146d5749c528b60643192da451e_14.png)

In our node type enum， we're going to add the while statement。



![](img/08fdd146d5749c528b60643192da451e_16.png)

Noode type， so while statement equals while statement。



![](img/08fdd146d5749c528b60643192da451e_18.png)

Then we'll scroll down to our statements。The very bottom of this region。

 I'll paste in the while statement for the sake of time。



![](img/08fdd146d5749c528b60643192da451e_20.png)

So this class is pretty similar to all the other statements。 We're going to take in a condition。



![](img/08fdd146d5749c528b60643192da451e_22.png)

So。IfI set this here。We're going to take in a condition， which is going to be our a。



![](img/08fdd146d5749c528b60643192da451e_24.png)

Less than or equal to or less than 10。 This convey air condition expression。



![](img/08fdd146d5749c528b60643192da451e_26.png)

Then we're going to take in a body， which is our block statement right here。 So everything that。



![](img/08fdd146d5749c528b60643192da451e_28.png)

S in the while loop。We're gonna set two variables， condition and body。 So if body is none。

 we'll set it to。An empty list。

![](img/08fdd146d5749c528b60643192da451e_30.png)

If not， it will set it to body。So we'll implement our type as well， type function to W statement。

 and then our debug JSON as well。

![](img/08fdd146d5749c528b60643192da451e_32.png)

![](img/08fdd146d5749c528b60643192da451e_33.png)

So we'll save that。 That's everything we need to do in AS T。 So we'll move on to our parser。



![](img/08fdd146d5749c528b60643192da451e_35.png)

As always， we'll go up here to our statements。 I'm going to create a new line here from A T。

Import while statement。

![](img/08fdd146d5749c528b60643192da451e_37.png)

Then we'll go down to parse statement method。So we'll look for that par statement。

 We're going to add while to here。

![](img/08fdd146d5749c528b60643192da451e_39.png)

Case， token type。

![](img/08fdd146d5749c528b60643192da451e_41.png)

Dot while。We return self dot or Sner score parse while statement。



![](img/08fdd146d5749c528b60643192da451e_43.png)

![](img/08fdd146d5749c528b60643192da451e_44.png)

Now， just as you probably guessed， we're going implement that function now。 So of statement methods。

 we' go to the very bottom of that region。

![](img/08fdd146d5749c528b60643192da451e_46.png)

Deaf parse wall statement， take in self。 and I'll return a while statement note。



![](img/08fdd146d5749c528b60643192da451e_48.png)

We'll set two variables， one for condition。

![](img/08fdd146d5749c528b60643192da451e_50.png)

It goes none and we'll set one for body。 It's a block statement， and we'll collect a none as well。



![](img/08fdd146d5749c528b60643192da451e_52.png)

So now when we get to this token， that means we're on the wild token。



![](img/08fdd146d5749c528b60643192da451e_54.png)

So in our test， I'll get our test line file up again。



![](img/08fdd146d5749c528b60643192da451e_56.png)

Here。So right now， the parser is at this wild token。 So we're going to advance to the next one。



![](img/08fdd146d5749c528b60643192da451e_58.png)

![](img/08fdd146d5749c528b60643192da451e_59.png)

So now we're at a。So now we're expecting an expression。



![](img/08fdd146d5749c528b60643192da451e_61.png)

So we're going to set condition equal to self。Dot parse expression。

And the precedes type will just set at the lowest。Value。



![](img/08fdd146d5749c528b60643192da451e_63.png)

Now that this parse expression is completed， we're expecting this left brace。 So if not。



![](img/08fdd146d5749c528b60643192da451e_65.png)

Self dot expect peak。

![](img/08fdd146d5749c528b60643192da451e_67.png)

And we're expecting a left brace token。 If not， we return none。 So we clearly have an error。



![](img/08fdd146d5749c528b60643192da451e_69.png)

If we do have that left brace， that means we are ready to start parsing a block statement。

 So we'll set body go to self dot underscore underscore score parse block statement。



![](img/08fdd146d5749c528b60643192da451e_71.png)

![](img/08fdd146d5749c528b60643192da451e_72.png)

![](img/08fdd146d5749c528b60643192da451e_73.png)

And then we'll return the while statement node， setting condition to condition。



![](img/08fdd146d5749c528b60643192da451e_75.png)

And body equal to body。

![](img/08fdd146d5749c528b60643192da451e_77.png)

And is just a quick thing that I remembered。 We'll go back into our A S T right here。

 This makes absolutely no sense。 We're saying this is a block statement。 yet， if it's none。

 we're setting it to an empty string， so。From the code I just wrote。It should never be none。

 So we're going get rid of that whole thing and just set it to body。



![](img/08fdd146d5749c528b60643192da451e_79.png)

So now that we have that out of the way， the while statement is done in the parser。



![](img/08fdd146d5749c528b60643192da451e_81.png)

So we'll move on into our compiler。

![](img/08fdd146d5749c528b60643192da451e_83.png)

In our our compiler， the first thing we'll do is scroll to the top。



![](img/08fdd146d5749c528b60643192da451e_85.png)

We'll make a new line from AS T。

![](img/08fdd146d5749c528b60643192da451e_87.png)

Import while statement。Will it go down to our compile method。



![](img/08fdd146d5749c528b60643192da451e_89.png)

At the very bottom of our statements little section。



![](img/08fdd146d5749c528b60643192da451e_91.png)

WeLet a case node type， dot while statement。

![](img/08fdd146d5749c528b60643192da451e_93.png)

Self dot underscore underscore， visit while。Statement， we'll pass in that node。

And you'd never believe it。 we're going to implement this while statement function。

 So in our visit statement methods block。

![](img/08fdd146d5749c528b60643192da451e_95.png)

![](img/08fdd146d5749c528b60643192da451e_96.png)

Scrolled to the very bottom。Right there， underneath if statement。



![](img/08fdd146d5749c528b60643192da451e_98.png)

Deaf visit while statement will take itself。 Also take in a node of type while statement。



![](img/08fdd146d5749c528b60643192da451e_100.png)

And this won't return anything。

![](img/08fdd146d5749c528b60643192da451e_102.png)

We're to start off with just kind of breaking out of our nodes。 So condition。Eals no dot condition。

bodydy。Not a blocking I O Air block statement。 No dot body。



![](img/08fdd146d5749c528b60643192da451e_104.png)

We're gonna test the condition。 So test dot underscoreca we don't care about the。



![](img/08fdd146d5749c528b60643192da451e_106.png)

Type we'll call our resolve value。So we're going to resolve the value of this condition to see whether it's true or false。



![](img/08fdd146d5749c528b60643192da451e_108.png)

We need to create a block。Where the as an entry to our while loop， If the condition is true。

 this is where the。Compiler would jump to to run the specific block of code。 So our wild loop。Entry。



![](img/08fdd146d5749c528b60643192da451e_110.png)

So you go to self dot builder， dot appendned basic block。



![](img/08fdd146d5749c528b60643192da451e_112.png)

We'll do an F string。 We'll call this block while loop entry， underscore。

Self increment counter and curly braces to add a number to that。 So if we have multiple while loops。

 we'll know， hey， this is the oneca we'll have a unique number each time。



![](img/08fdd146d5749c528b60643192da451e_114.png)

If the condition is false， we need a otherwise block。 So wall loop otherwise。

 So the program will jump to this block of code。 if the condition is false。



![](img/08fdd146d5749c528b60643192da451e_116.png)

![](img/08fdd146d5749c528b60643192da451e_117.png)

So the same as before self dot builder， pen basic block， F string， while loop。Otherwise， underscore。



![](img/08fdd146d5749c528b60643192da451e_119.png)

And then we'll set it to our counter value that it is now。

 since we already called it here to increment it。

![](img/08fdd146d5749c528b60643192da451e_121.png)

![](img/08fdd146d5749c528b60643192da451e_122.png)

I will paste in this little bit of commenting just to help it out。

 We're making a condition branch very similar to how we do in the F statement。



![](img/08fdd146d5749c528b60643192da451e_124.png)

![](img/08fdd146d5749c528b60643192da451e_125.png)

We're going to create a self dot builder do C branch。



![](img/08fdd146d5749c528b60643192da451e_127.png)

Since it's a conditional branch。First thing'， the condition。 So that's our test value。



![](img/08fdd146d5749c528b60643192da451e_129.png)

If it's true， we want to branch to the wild loop in tree block。 If it's false。

 we want a branch to our otherwise block。

![](img/08fdd146d5749c528b60643192da451e_131.png)

![](img/08fdd146d5749c528b60643192da451e_132.png)

And then we're going to set our builder's position。



![](img/08fdd146d5749c528b60643192da451e_134.png)

At the start of the while loop entry block。

![](img/08fdd146d5749c528b60643192da451e_136.png)

We are going to compile the body of the while statement。We're going to test the。

So this this is what's happening in the while loop entry block。 So we're going to compile the body。

So this is as if it were true。 We're compiling the body。 It's running the body。



![](img/08fdd146d5749c528b60643192da451e_138.png)

And then we're going to test the condition again， because the body is over。

So test underscore self dot resolve value or resolve that condition again。



![](img/08fdd146d5749c528b60643192da451e_140.png)

If it's still true。It will jump right back to the entry。 If not， itll go to otherwise。

 So we'll have another C branch， condition branch。

![](img/08fdd146d5749c528b60643192da451e_142.png)

If that value is true， we're go into the entry block， if it's false。



![](img/08fdd146d5749c528b60643192da451e_144.png)

Weor leaving the wild loop and going otherwise。And then we will position our builder。

At the while loop otherwise position。 So everything that happens after the block。 So in our case。

 return A， this boy will be ran。Once this wildly bear is finished。After that。

 that should be absolutely everything we need。 So we will。



![](img/08fdd146d5749c528b60643192da451e_146.png)

Bring this test dot line up。 Go down to our terminal with our Python environment。Activated。

 and we'll type in Python main dot pi。

![](img/08fdd146d5749c528b60643192da451e_148.png)

So program return 10。

![](img/08fdd146d5749c528b60643192da451e_150.png)

And here we are。 we have 0，1，2，3，4， all the way down to 10。 This program return 10。



![](img/08fdd146d5749c528b60643192da451e_152.png)

And it did not print 10 because a was 10 and 10 is not less less than 10。

 So it broke out when it was supposed to and returned it out。So we'll run again for fun。Really quick。

1 millisecond here， so。There it is。 There is the while loops。

 and you can do just about anything you want in these wild loops。

 You can create an infinite loop and break your computer。 if you'd like， It does not matter。



![](img/08fdd146d5749c528b60643192da451e_154.png)

![](img/08fdd146d5749c528b60643192da451e_155.png)

But thank you guys for watching。 That was Wild loops。In our next episode。

 we're going to be going into adding continue and break keywords to our language and then implementing them so we can break out early of while loops。

So if I were to do if one equals  one or if a equals 5 or 4。We can break out。

Or if I just really don't like if。A equals 2。 If I really just don't like the number 2。

I could just continue on the loop。We'll do that before we print because I don't want to print to。

That's what we'll be implementing in the next。Episode as well as four loops to kind of cap off all of the different types of loops for our language。

Thank you for watching。And I will see you in episode 13。



![](img/08fdd146d5749c528b60643192da451e_157.png)
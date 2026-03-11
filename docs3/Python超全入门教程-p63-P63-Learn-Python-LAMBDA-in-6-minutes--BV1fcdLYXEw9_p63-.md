# Python超全入门教程-p63-P63-Learn-Python-LAMBDA-in-6-minutes--BV1fcdLYXEw9_p63-

Yo， what's going on， everybody。 So today， I'm going to discuss Lambda functions in Python。

 A lambmbda function is a small anonymous function for of one time use。 Then we throw them away。

 They take any number of arguments， but only have one expression。

 A few of the benefits of lambda functions is that they help keep the namespace clean。

 because we don't have to think of a unique name for that function。 We're only going to use at once。

 We don't need to give it a name。 And they're useful with something called higher order functions。

 which we still need to talk about。 their sort map filter and reduce， for example。

 Here's an example of a lambda function that you may see within a map method。 We have lambmbda。

 Our parameters。 colon， our expression。 I haven't talked about the map function yet。

 A lambda function is a function you would commonly see within the map function。

 a higher order function。 but that's a topic for a future video。 In this video。

 we're going to focus more on these syntax of lambda functions。😊。



![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_1.png)

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_2.png)

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_3.png)

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_4.png)

So what we'll do is we will create a variable。Let's say double。

We'll write a lambda function to double a number following this formula。

 We have to type the key word Lambda to specify that this is a lambda function。

 We have our parameters。 We will accept one parameter， which we will name X colon。

 then a one line expression。Let's say with X， I would like to double it。 X times 2。

So what we're doing is we're assigning a Lambda function to a variable。

 although you could assign a Lambda function to a variable， that's not the primary use of them。

 you would more likely see Lambda functions within higher order functions。



![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_6.png)

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_7.png)

Like I said， we're just covering the syntax of the lambmbda function。With this variable of double。

 it contains a function， meaning we can call it to demonstrate that。

 I'm going to print my double variable since it contains a function within it。We can call it。

 We have to pass in one argument。 Let's say two。 We will double 2 and print the result。

 which gives me 4。 If I were to double 3， that would give me 6。 If I doubled 4， that gives me 8。



![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_9.png)

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_10.png)

With lambda functions， we can have any number of arguments。 This time， we'll create two arguments。

 We will assign a variable of add and add two numbers together with the lambda function。



![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_12.png)

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_13.png)

Lambda， our parameters are x， comma Y， colon， then our expression。 Let's add x and y together。



![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_15.png)

X plus y。

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_17.png)

I will take my variable of add。 It contains a function within it。 I can call it。

 but I have to pass into arguments for x and Y。 Let's add2。And 3。

Then we have to print it in order to see it。

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_19.png)

And the result is 5。

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_21.png)

Let's write a more complicated expression。We'll find the greater of two numbers。

I will create a variable of max value。Equals again， following this formula。Lambda。

Then we need the parameters。 We'll compare two numbers， X and Y。

We'll return x if x is greater than y。Else， we will return why this is similar to a list comprehension。



![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_23.png)

I will print。 Take my variable of max value。Call the lambmbda function that's within it。

 Pass in two numbers。

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_25.png)

What is the greater number between 4 and 5。5ve。😡，What about six and five？Well， we get six。Okay。

 let's do the opposite。 Let's find the minimum value。We have X and y。Return x if x is less than y。

Else why。What is the minimum value between6 and 7？

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_27.png)

s。😡。

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_29.png)

What about between8 and7？7even。We' create a lambda function to concatenate a string。

 I will create a variable a full name equals lambda。 We will have two parameters。 first。

 meaning first name and last， meaning last name。We'll take our first name。First， plus a space。

 plus the last name。

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_31.png)

I will print our full name variable。Called the Lambda function。 That's within it。

Pass in a first name and a last name。I will pick Sponongebob。Last name， Squarep。



![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_33.png)

This will give me a full name of Spongeboob， space， square pants。



![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_35.png)

All one long string because we're using string cacatenation。



![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_37.png)

Using a Lambda function， we can check to see if a number is even。



![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_39.png)

I will create a variable of is even。This will give us a bulloleion。Lambda。X will be the parameter。

 X modulus 2。Modulus gives you the remainder of any division。If x is divisible by 2。

 that means there is going to be no remainder。 We can check to see if that is equal to 0。So。

 I will print。R is even variable。 Call the lambmbda function that's within it。

 Let's see if the number 4 is even。

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_41.png)

Four divides by two evenly， that's true。But what about five？



![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_43.png)

That's false。Let's do an age verification check。 I will create a variable of age check equals Lambda。

 We have one parameter of age。I will return true。If our age is greater than or equal to 18。Else。

 we will return false。I will print our age check variable。And pass in 21。



![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_45.png)

That returns true。But what about 12。

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_47.png)

That returns false。Art everybody。 So those are lambmbda functions。 They're small。

 anonymous functions for a one time use。 They take any number of arguments。



![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_49.png)

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_50.png)

But only have one expression using Lambda functions helps keep the namespace clean because we don't need to constantly think of different function names。

 especially within a larger program。 And they're extremely useful with something called higher order functions。

 such as sort， map， filter and reduce， which we'll be covering in the next few videos。 And well。

 everybody， those are Lambda functions in Python。

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_52.png)

![](img/ee0d25f7d46e9e6970b7daf7e6cfb000_53.png)
# Python超全入门教程-p28-P28-Lets-code-a-Python-NUMBER-GUESSING-GAME--BV1fcdLYXEw9_p28-

Hey， everybody。 So today we're going to create a number guessing game using Python。

 This is a project meant for beginners By completing this project。

 it will help us reinforce our understanding of previous topics。 Let's begin。😊。



![](img/c4b89b28761031c14dd4b1973d1bd265_1.png)

We will import the random module。We'll need to pick a random number。

 The random module is going to handle that for us。What is the range of random numbers for our number guessing game？

 We'll store those as variables。We will have one variable named lowest number。

 I'll set that to be one。As well as a variable for highest number。Which I will set to be 100。

 Feel free to pick a different range， if you would like。 I'll set the range to be 1 through 100。

 A random number will be selected between this range。

Which will be stored within a variable named answer。 What is the correct answer。

So to choose a random number between these two values。We will access the random module。

Call the Rand int method。We will choose a random integer between these two values。

The two arguments will be lowest nu， comma， highest nu for the second argument。

Let's perform a test run。 I will print my answer。The number is going to be between one and 100。Okay。

 we know that that works。Here's a few more variables。

We need to keep track of the number of wrong guesses， which I will store as a variable named guesses。

We want the user to keep guessing as long as our application is running。

We will create a Boolean variable of is running， which we will set to be true。

Once the user wins the game， we will set is running to be false。We will print a welcome message。

Let's say， Python number。Guessing game。We will prompt the user。 I'll use enough string。

Select a number between。I'll add two placeholderers。

Select a number between our lowest number and our highest number。

Python number guessing game select a number between 1 and 100。



![](img/c4b89b28761031c14dd4b1973d1bd265_3.png)

Now， if I was to change the range of these variables。That should be reflected。



![](img/c4b89b28761031c14dd4b1973d1bd265_5.png)

Temporarily， I changed the lowest number to be 10 and the highest number to be 1000。

 but let's set that back。

![](img/c4b89b28761031c14dd4b1973d1bd265_7.png)

Between one and 100 is good。We'll need a while loop to continue the game each round。



![](img/c4b89b28761031c14dd4b1973d1bd265_9.png)

We will say， while is running。Since is running as a booleion。

 we don't need to say while is running equals true， we can just say while is running。

 while this value remains true， continue playing the game。We will ask the user for some input。

 We will create a local variable of guests。Gues equals。Use the input function。Then enter a prompt。

Enter your guess。

![](img/c4b89b28761031c14dd4b1973d1bd265_11.png)

There's one thing we want to check。Python number guessing game。

 select a number between 1 and 100 and to your guess。

 What if somebody doesn't type in a number like they type in the word pizza。

We should let the user know that that's an invalid guess。



![](img/c4b89b28761031c14dd4b1973d1bd265_13.png)

We'll write the following if statement if our guests use the is digit method。If our guest is a digit。

 a number。Then we will execute any code underneath this if statement for the time being。

 I'll write pass。 We'll get back to that later。Else， we will do something else。

Let's print the following。Print， invalid。

![](img/c4b89b28761031c14dd4b1973d1bd265_15.png)

Guess。Let's copy this print statement because I'm lazy and I don't feel like typing it out。



![](img/c4b89b28761031c14dd4b1973d1bd265_17.png)

Please select。A number between our lowest number and our highest number。



![](img/c4b89b28761031c14dd4b1973d1bd265_19.png)

Let's try that again。I will guess pizza， which isn't a number。And we get the message invalid guess。

 Please select a number between 1 and 100。

![](img/c4b89b28761031c14dd4b1973d1bd265_21.png)

All right， that works。Underneath our if statement， we'll write the following。



![](img/c4b89b28761031c14dd4b1973d1bd265_23.png)

Once we get a guess that is a digit， we need to convert it to a number because when you accept user input。

 it's a string。We will reassign our guests equal to Tcast our guess as an integer。

Then increase the number of guesses by one guesses plus equals one because we have already made one guess。



![](img/c4b89b28761031c14dd4b1973d1bd265_25.png)

![](img/c4b89b28761031c14dd4b1973d1bd265_26.png)

Here's another scenario。What if somebody guesses a number outside of this range， like one cajillion。



![](img/c4b89b28761031c14dd4b1973d1bd265_28.png)

Well， we should give a warning that back death isn' invalid。



![](img/c4b89b28761031c14dd4b1973d1bd265_30.png)

If our guess is lower than the lowest number。Or our guess is greater than the highest number。



![](img/c4b89b28761031c14dd4b1973d1bd265_32.png)

We will print the following。That number is out of range。



![](img/c4b89b28761031c14dd4b1973d1bd265_34.png)

And I will repromp the user。

![](img/c4b89b28761031c14dd4b1973d1bd265_36.png)

Please select a number between the lowest number and the highest number。



![](img/c4b89b28761031c14dd4b1973d1bd265_38.png)

Let's perform a test run。

![](img/c4b89b28761031c14dd4b1973d1bd265_40.png)

I will guess，1 cajillion。That number is out of range。 please select a number between 1 and 100。



![](img/c4b89b28761031c14dd4b1973d1bd265_42.png)

We'll add an Elsev statement else， if a gas。Is less than our answer。We will print the following。

Too low。Try again。Else， if。Our guess is greater than our answer。We will print。Two， hi， try again。



![](img/c4b89b28761031c14dd4b1973d1bd265_44.png)

If our guess isn't less than our answer and our guess isn't greater than our answer。

 that means we must have the correct answer。

![](img/c4b89b28761031c14dd4b1973d1bd265_46.png)

Within an out statement。

![](img/c4b89b28761031c14dd4b1973d1bd265_48.png)

We will print。I'll use enough string。Correct。The answer was insert our answer， our answer variable。

Then print the number of guesses it took。Number of guesses。Add a playholder。

Place in our guesses within the placeholder。 Now， to escape the while loop。

 we will take our Boolean variable of is running， which is normally true。



![](img/c4b89b28761031c14dd4b1973d1bd265_50.png)

![](img/c4b89b28761031c14dd4b1973d1bd265_51.png)

And set that to be false， to escape。

![](img/c4b89b28761031c14dd4b1973d1bd265_53.png)

And that should be all we need。 Let's run this one last time。



![](img/c4b89b28761031c14dd4b1973d1bd265_55.png)

Python number guessing game select a number between 1 and 100。

Let's select a number right in the middle，50。Too low。 try again。 So the number is between 50 and 100。

75。Too high。It's between 50 and 75， then。62。Too high。56。53。55。Correct。

 the answer was 55 number of guesses。 It took me 6。



![](img/c4b89b28761031c14dd4b1973d1bd265_57.png)

All right， everybody。 that is a Python number guessing game you yourself can create as a mini project。



![](img/c4b89b28761031c14dd4b1973d1bd265_59.png)
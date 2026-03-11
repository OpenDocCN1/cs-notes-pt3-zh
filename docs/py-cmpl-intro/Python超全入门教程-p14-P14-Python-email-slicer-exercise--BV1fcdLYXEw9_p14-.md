# Python超全入门教程-p14-P14-Python-email-slicer-exercise--BV1fcdLYXEw9_p14-

Everybody， in this topic， we're going to create an email slicer program。

 I was going to create this program as an exercise at the end of our string indexing video。

 but I completely forgot。 So I'm gonna make a separate video on it。

 It's a fairly straightforward program。 It won't take too many lines of code。 Allright， let's begin。

 We'll accept some user input。😊。

![](img/7146291205a13f306b1523a6127ad869_1.png)

![](img/7146291205a13f306b1523a6127ad869_2.png)

We will store this as a variable named email email equals input will create a prompt enter your email。



![](img/7146291205a13f306b1523a6127ad869_4.png)

For my email example， let's say my email is bro 1，2，3 at Gmail dot com。

 There is a built in method of strings called the index function。

 This function index will return the first instance of a character。

 Let's find the index of our a symbol。 We'll split the email by user name and domain。

 But we need to know where to split it exactly at this at symbol。

 So we will find our index of that at symbol。

![](img/7146291205a13f306b1523a6127ad869_6.png)

![](img/7146291205a13f306b1523a6127ad869_7.png)

Equals。Take our email。 Our email is technically a string。 So there is a built in index method。

 We will find the index。

![](img/7146291205a13f306b1523a6127ad869_9.png)

![](img/7146291205a13f306b1523a6127ad869_10.png)

Of our at symbol。This method will return a number。 We will create two new variables， user name。



![](img/7146291205a13f306b1523a6127ad869_12.png)

![](img/7146291205a13f306b1523a6127ad869_13.png)

As well as domain。Username equals our email。 We will use the indexing operator。 Then place a colon。

 So where do we begin an end with the user name？ Well， with Python。

 we don't need to specify the beginning of a string。 You could say 0， but we can omit that。

 but we do need an ending index， and that would be our index variable。



![](img/7146291205a13f306b1523a6127ad869_15.png)

![](img/7146291205a13f306b1523a6127ad869_16.png)

![](img/7146291205a13f306b1523a6127ad869_17.png)

With our domain， we can take the other half of our email。



![](img/7146291205a13f306b1523a6127ad869_19.png)

이mail。

![](img/7146291205a13f306b1523a6127ad869_21.png)

Index of operator。Where do we begin and end， Well， we will begin where we left off index。



![](img/7146291205a13f306b1523a6127ad869_23.png)

Index by itself isn't going to work， as you would think， and I'll demonstrate why。



![](img/7146291205a13f306b1523a6127ad869_25.png)

Then let's print using an F string。Your user name is。Our placeholder。Username。And domain is。

Our domain variable。

![](img/7146291205a13f306b1523a6127ad869_27.png)

Okay， let's test this。En to your email， bro 1，2，3 at Gmail。 com。 Feel free to use your own email。



![](img/7146291205a13f306b1523a6127ad869_29.png)

Your username is bro 1，2，3， and domain is at Gmail dot com。

 I would like to omit this at symbol at the beginning of my domain。

 What we'll do when we assign our domain variable is set the beginning index to index plus one。

 Then we will start after the a symbol。

![](img/7146291205a13f306b1523a6127ad869_31.png)

![](img/7146291205a13f306b1523a6127ad869_32.png)

![](img/7146291205a13f306b1523a6127ad869_33.png)

So bro，1，2，3 at Gmail。com。Yeah， here we go。 Your user name is bro 1，2，3， and domain is Gmail dot com。

 If you would like to take less lines of code， here's how let's copy this index function。



![](img/7146291205a13f306b1523a6127ad869_35.png)

![](img/7146291205a13f306b1523a6127ad869_36.png)

![](img/7146291205a13f306b1523a6127ad869_37.png)

Delete our index variable。 replace index with that function。



![](img/7146291205a13f306b1523a6127ad869_39.png)

So let's test this with a new email。 bro， blah， blah， blah， blah，1，2，3，4，5，6 at Gmail dot com。



![](img/7146291205a13f306b1523a6127ad869_41.png)

![](img/7146291205a13f306b1523a6127ad869_42.png)

That's a very long username。

![](img/7146291205a13f306b1523a6127ad869_44.png)

And domain is Gmail dot com。 This style would work as well。 However， it's less readable。

 but it does take less lines of code。 So it's up to you how you'd like to write this。

 It's personal preference。 But yeah， I thought that'd be a nice exercise。

 Now that we know how string indexing works。 And like I said。

 I forgot to include this exercise at the end of that string indexing video。

 But a separate video on this topic wouldn't be bad either。 But yeah， everybody。

 that is a email slicing program in Python。

![](img/7146291205a13f306b1523a6127ad869_46.png)

![](img/7146291205a13f306b1523a6127ad869_47.png)

![](img/7146291205a13f306b1523a6127ad869_48.png)

![](img/7146291205a13f306b1523a6127ad869_49.png)

![](img/7146291205a13f306b1523a6127ad869_50.png)
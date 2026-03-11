# Python超全入门教程-p13-P13-String-indexing-in-Python-is-easy--BV1fcdLYXEw9_p13-

Hey， everybody， in this topic， I'm going to explain string indexing。

 Ining allows us to access the elements of a sequence using a set of square brackets。

 also known as the indexing operator using this set of square brackets following a string。

 There are up to three fields that we can fill in。 We can access a starting point in the string an ending point at a step。

 Here's an example。 Suppose we have a credit card number。 credited。😊。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_1.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_2.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_3.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_4.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_5.png)

Number equals。 And I'll just make up some number 1，2，3，4， dash，5，6，7，8， dash 9，0，1，2， dash 3，4，5，6。

 Good enough。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_7.png)

If I need the first character within the string， I can type the name of my string variable。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_9.png)

Followed by the indexing operator， which is a set of square brackets。

 The first position has an index of 0。 Computers always start with 0。

 So that's why the first index is 0。 Then I'm going to go ahead and print this。

 Pri credit card number at index of 0。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_11.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_12.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_13.png)

That would be one。 if I were to change the index to be 1，0，1， that should be 2， index 2。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_15.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_16.png)

Would technically be three。Then4 is the dash within our string， as you can see here。

 with the indexing operator， there's up to three fields that we can fill in a start and a step。

 If you have just one field listed without any colons。

 it's assumed you're filling in the starting position。 So now。

 what if you would like the first four digits of the string。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_18.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_19.png)

Well， we would type the name of our string variable。Indexing operator。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_21.png)

We'll need a starting index。Colon， then an ending index。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_23.png)

The first four digits would be 0， colon。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_25.png)

4our。😡，Then， I will print this。And I'm just going to turn this first line into a comment。Yeah。

 there we go。 We have the first four digits of our credit card number，1，2，3，4。

 Just so you know with the ending index， this index is exclusive。 This first number would be 0，1，2，3。

4。 So we did not include that dash within the number。 The starting index is inclus。

 The ending index is exclusive， so you can omit the 0 in the beginning。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_27.png)

You could just say colon 4 Python assumes the starting position will be the beginning of the string。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_29.png)

So that would work too。Let's get the next set of digits，56，7，8。Credit number。Indexing operator。

 let's find where the starting index would be 0，1，2，3，4，5。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_31.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_32.png)

5， colon，6，7，8，9。Then we will print whatever is here。The next set of digits is 5，6，7，8。

 Maybe we need the last 12 digits。 Well， what we could do in that case。

 We will take our string variable credit number。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_34.png)

Set the starting index to be， let's see，0，1，2，3，4，5。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_36.png)

5 colon。 if you need everything up to the end of the string， you don't need to list an ending index。

 Just be sure to add that colon。 Python then assumes you need everything up to the end of the string。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_38.png)

So I will print whatever we have。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_40.png)

Then we should have everything besides the first four digits。 Yep，5，6，7，8，9，0，1，2，3，4，5，6。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_42.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_43.png)

You could also use a negative index。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_45.png)

Credit number。 If you need the last character in a string， you would set the index to be negative1。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_47.png)

Then， I will print this。Print credit number at index of negative one。 That would be 6。

Negative 2 is 5。Negative 3 is 4。Negative 4 is 3， and then negative 5 would be that dash right here。

 Yeah， you can use negative indexes， too。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_49.png)

Let's talk about step using the step field。 We can access the characters in a string by a given step。

 We can count by twos。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_51.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_52.png)

Or we can count by threes。 So here's an example。 So let's take our credit number。

 If we're not filling in these starting or ending fields， but we need a step。

 we would need two colons。 Then Pyon is assuming everything from the beginning of the string to the end。

 then。 our step will be 2。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_54.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_55.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_56.png)

This will print every second character within our string。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_58.png)

Yeah， here we are。 We have1，3， dash，6，8，9。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_60.png)

1， so on and so forth。If I were to change these step to three。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_62.png)

We would count every third character， beginning with one。4our。6 dash。1，3，6。 All right。

 here's a practical example。 Let's create a program to get the last four digits of a credit card number。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_64.png)

I'm going to assign this to a new variable。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_66.png)

Last。Digits。Equals。Our credit number。Indexing operator。 So we need the last four digits。

 Where would the starting index begin， Well， we could use negative indexing。

 This last digit is negative 1， negative 2， negative 3， negative 4。 We will begin at negative 4。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_68.png)

Colin。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_70.png)

We can't omit the ending index。 Python assumes we need the rest of the string。 Then。 Really。

 that's all we need。 So let's print。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_72.png)

I'll use enough string。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_74.png)

Maybe some x's， maybe we're hiding somebody's credit card number except the last four digits。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_76.png)

Okay， then variable last。Digits。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_78.png)

All right。 And here's our credit card number where only the last four digits are visible。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_80.png)

Hey， you know what。 Let's add one more exercise。 Let's reverse the characters in the string。

 I'm going to a reassign credit number。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_82.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_83.png)

Equals credit number。

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_85.png)

If we need the entire string， we don't necessarily need a starting index or an ending index。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_87.png)

But for the step， this will be negative。 Ne one will reverse a string。

 Then let's print whatever our new credit card number is。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_89.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_90.png)

Print。Credit number。And yeah， there is our credit number backwards。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_92.png)

To reverse a string， you set the step to be negative 1。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_94.png)

So yeah， everybody， that is string indexing in Python。

 We can access elements of a sequence using the indexing operator。

 which is a set of straight brackets。 You can list a starting position， ending position。

 and even a step。 if you need to skip over characters。 But yeah， that is string indexing in Python。😊。



![](img/6226ceffd1877cb6d4ca89bad8eb77a8_96.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_97.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_98.png)

![](img/6226ceffd1877cb6d4ca89bad8eb77a8_99.png)
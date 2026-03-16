# 【加州大学】Go语言编程-｜-Go-Programming-Everyone-Part-2-p04-P04_学生_01_02_03--BV1GTe7z3Eqi_p4-

![](img/de7904aef315bdacf4ef80d14ac3804d_0.png)

And now we're going to do more with structures。And a way to do more with structures is to make use of what we call composition composition is a very powerful way to build and maintain complicated data structures。

So。If you had， for example。A structure that was already a person。

And that person may even have substructures as part of its members。

Then you could use the person structure to build a student structure。

So you would already have lots of routine and code that would work on person。

 and then it would all of a sudden be available to help you work on student。So。

It turns out that more powerful languages like C++ that employ object orientation also employ composition and after a long time of working with both object。

Orientation， which involves inheritance to build complex structures。It can turn out that composition。

 which is an earlier style of building complicated data structures。

 is actually easier to maintain than what you find with inheritance。Okay。

 so we're going to look at building a student from a person。

So here we first have a straightforward struck for a name。

 and the name has just got a first name and a second and a last name and both of those are type string。

And we use that， again， composition to build person in person now as a struck。

In which one of the fields is of type name。And then we also allow for an address。

 which will be a string， and we allow for a grade point average。Now， person by the way。

 would have many uses， for example， if you were building an employee system or almost anything you could imagine。

 you might want to start with person。And use it to build whatever more complicated software you might need。

 but we're going to think about student and so student is of course， a person。

And a student takes tests， so they'll have test scores。

 and in this case it'll be a slice of integers。And then。

We have a way of taking those test scores and figuring out the student's grade point average。

So that's what a student will look like and notice how composition worked。

To build increasingly more complicated data structures。So now let's see how we might use that。

So in the previous slide。We built a complicated data structure。And some OO languages。

 if you have some experience might use inheritance， but in fact。

 composition and go chose to avoid being object oriented。

 so in go you don't have a choice if you're going to build complicated data structures your strongest tool is indeed composition。

 so the choice is made for you。And we'll see how to use it now so here for example。

 we're going to input the scores into a student， so we have a student we're pointing at it and then we'll have a certain number of test scores。

So you might have different classes and some classes might have many scores， many tests。

 and other classes might have relatively few， so we're building this as an indefinite number which will be inputted for a student。

 their test count。And now we'll ask for those scores。And print them out。And then for each score。

 we will read it into the student， the individual student test score。

 and finally we'll print those out so that we see that we have in fact。

 got those scores and notice that，Asking inside a loop。Up to test count。

And I do a scan app for each score， so that's where I'm prompted。

 you'll see it later when I run the program， I'm prompted for each individual test score。

 I enter them， and then that becomes part of the student。Record。Okay。

 let's see some more of the code。Now we have。Again， instead of a normal funk。

 we have what's called a method。And a method。Is very typical way to write code when you havestructs。

 because the method can be of， we can think of them as the verbs。That work with thosestructs。

 So one of the things we want to do with a struck student is to do a test average。

 And the way we'll do a test average is will some。The scores。

 and will sum them over the range of however many scores were in the field E do test score。

 Remember that that's a slice。And this type of foresstatement。

You might call it an iterator so you don't have to worry about indexing and we just add each element which ends up in turn being associated with the variable V into the sum。

 and then we get the grade average which is just。The integer divide of the sum over the number of test scores。

And we chose there a length。And the reason for that again， was that lets us use。Dynaically。

 however many test scores。We store it in that slice。Okay。

So now we actually will proceed and we'll create a person。Well， there's a person's last name。

 it's Coder and a first name is Kate， so that person's name will be Kate Coder。

 and then we'll declare a student。And that student will have an address in this case， the North Pole。

 and student will have an age， so if may be age 29， and there we show the student person。

Will be the person we created before namely Kate Koder。

 so we created a we created a student from a person and now we'll try to enter the grades and determine the test average。

So。We've been using pointers to the struck。Remember， a pointer is just an address of a variable。

 so here it's the address of the student variable S。We get a test count， we ask for the test count。

 that's going to be inputted， so we do a scan F and we input it into ampersand test count。

And then we make。Inside the struck for that student。The number of test scores we need， the slice。

 the size of the slice will be。Remember how make works， make dynamically allocates。

Test count number of integer variables into that slice。

 and that'll be stored in SOT test score for that student， so again this is dynamic。

We input the test scores。And that was a previously written function。And we can show what they are。

 we can print it out， make sure we get it right， and then we're going to use this method with taking a pointer to student。

 test average。We'll get the test average which will now show up and that students now be computed and that student's struck and then we'll print it out。

Okay。So notice how we've done all this and we will go to the terminal to execute this program and show that it actually works。

Okay， so let's again， look at that program， which I have coded in。Already。Okay。

 here again is our implementation name first， first and last， type person who address age。

 type student person。A set of test scores， a grade average。Here's our function that。

Computes to test average， and it's a method。So you can see that the first argument is appointed to student。

 and then we do a sum over the range of test scores。

 we get an average and store it into the field that's the great average field for that student。

We have the input the scores， so here in the input statement。We asked for a test count and then。

For as many。Casszo are in that class。We do a scanf， grab the score and store it in。

The students test slice。Then we have a method for printing a student。

And here we have mainine where we create。Kate Coder， living at the North Pole， age 29。And。

We're going to then ask for how many tests from the instructor， etc。

 and then do the calculations and print out so that's pretty much the program as we already discussed in detail again I recommend you yourself play with such a program or modify it you can add more fields to a student a student might also have。

An on campus major or a student might have a year， like a sophomore year。

 so there's other information you can certainly add。Now， run that。So it's again， first thing it does。

 how many tests？Okay， let's do four tests。I tell it four then it says input four scores for the student Kate Coder。

So I could be also， you could modify that program to do it for far more students。

So let's give her some scores。Kate Koder is a pretty good student。So there's the four score， 66， 77。

 9995。Apparently wasn't studying that much at the beginning of the class， but then。

Towards the end of the class paid a lot more attention so here we got the information we see that the test scores showed up。

 we see Kate codeder's。Name and address and age， so that was the person Kate Coder。

And then in student and scores， we have Kate Koder。The person。

 but we also have Kate Koder with their test scores and their average， which turned out to be 84。

All worked。あ。Again。A demonstration of how powerful it is in go to use。

Composition and building more complicated structures。All right。



![](img/de7904aef315bdacf4ef80d14ac3804d_2.png)

![](img/de7904aef315bdacf4ef80d14ac3804d_3.png)
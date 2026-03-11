# Python超全入门教程-p59-P59-Learn-Python-CLASS-METHODS-in-6-minutes--BV1fcdLYXEw9_p59-

Hey， what's going on， people。 So today， I've got to talk about class methods and Python。

 A class method allows operations related to the class itself。 They take C。

 L S as the first parameter， whereas instance methods will take self。

 self refers to any object created from that class。 C， L S， meaning class refers to the class。

 not any objects。 Here's an example。 We will create a class。Of student。

We'll need a constructor to construct some student objects。All students will have a name。And a GP。

Self dot name equals name。Self do GPA equals GPA。We will also create a class variable for this demonstration of count。

 We will count how many students we create。Whenever we construct to student object。

We will access the class of student。 Take our count variable， incremented by one。

Whenever we create a student object， increase count by one。I will create an instance method。Of get。

Info。Instance methods have self as the first parameter。

We're referring to the object we're currently working with。I will return。



![](img/5bfb5bb56c14c748bea4c8745236b37a_1.png)

An F string。Where we will display the student's name and their GPA。Self dot name。Self dot GP。

I'll add a comment。That this is an instant method。Now to create a class method。

To work with class data， we will declare a class method with a class method decorator。



![](img/5bfb5bb56c14c748bea4c8745236b37a_3.png)

Class method。

![](img/5bfb5bb56c14c748bea4c8745236b37a_5.png)

What we're going to do is to find a method to get the count， the class variable of count。



![](img/5bfb5bb56c14c748bea4c8745236b37a_7.png)

This method will be called get count。Rather than self as the first parameter。

 we'll be working with a class， CS。Meaning class。I will return enough string。

Total number of students。Add a placeholder。CLs count。Let's test this。To call a class method。

 you take the name of the class followed by the class method。Get count。

And then we do need to print this。

![](img/5bfb5bb56c14c748bea4c8745236b37a_9.png)

What is the account of my current students， total number of students is zero。



![](img/5bfb5bb56c14c748bea4c8745236b37a_11.png)

Let's create a few student objects。We will create student one equals called the student Conor。

 We have to pass in a name and a GPA。 Let's say that the name is SponongBob。 SpongBob has a GPA of 3。

2。We'll create two more students。Student 2， Student 3， Student 2 will be Patrick。Patrick has a 2。0。

Then， Sandy。Sandy smart， in fact， she's a genius。She has a perfect 4。0。

Now let's count the number of students。Total number of students is3。When we call this class method。



![](img/5bfb5bb56c14c748bea4c8745236b37a_13.png)

We can access or modify class data this class variable of count。



![](img/5bfb5bb56c14c748bea4c8745236b37a_15.png)

Rather than using self， we use CLS for the class。

![](img/5bfb5bb56c14c748bea4c8745236b37a_17.png)

Let's create one more class method。

![](img/5bfb5bb56c14c748bea4c8745236b37a_19.png)

This time I'll calculate the total GPA of all my students。

We'll need a class variable to hold that data。Let's say total GP equals 0。



![](img/5bfb5bb56c14c748bea4c8745236b37a_21.png)

Whenever we construct a student object。We will access our class of student， get the total GPA。



![](img/5bfb5bb56c14c748bea4c8745236b37a_23.png)

Then add plus equals this student's GPA that we have just created。Basically speaking， the total GPA。

 this variable is going to accumulate all of the GPA of every student and store it as a sum。

To find the average， we're going to divide it by the count， the number of students。



![](img/5bfb5bb56c14c748bea4c8745236b37a_25.png)

We'll do that within a class method。

![](img/5bfb5bb56c14c748bea4c8745236b37a_27.png)

To create a class method again， we need to use the class method decorator。



![](img/5bfb5bb56c14c748bea4c8745236b37a_29.png)

I will define a method of get average GP。 The first parameter is CLS for class。

I will check if CLS count the count variable of my class。Is equal to 0。

 That means if we have no students， if that's the case， if there's no students。

 we're going to return 0。

![](img/5bfb5bb56c14c748bea4c8745236b37a_31.png)

Because otherwise we're going to divide by zero and we'll get an error。Else。

 we're going to return an F string。

![](img/5bfb5bb56c14c748bea4c8745236b37a_33.png)

Follow this formula。We're going to take the total GP of my class。

 class do total GPA divided by class do count the number of students we have。



![](img/5bfb5bb56c14c748bea4c8745236b37a_35.png)

That's how to calculate the average GPA。

![](img/5bfb5bb56c14c748bea4c8745236b37a_37.png)

After getting the count of the number of students， tax is a class method。

 we take the name of the class student。

![](img/5bfb5bb56c14c748bea4c8745236b37a_39.png)

Call the class method， get average GPA。

![](img/5bfb5bb56c14c748bea4c8745236b37a_41.png)

Then I will print it。

![](img/5bfb5bb56c14c748bea4c8745236b37a_43.png)

Total number of students is 3， the average GPA is 3。06 repeating。



![](img/5bfb5bb56c14c748bea4c8745236b37a_45.png)

After calculating the average， I'm going to add a format specifier of 0。2 F。

Just around to two decimal places。And I'll add average GPA colon in space。

 then we'll calculate the average。

![](img/5bfb5bb56c14c748bea4c8745236b37a_47.png)

All right everybody， those are class methods。Instance methods are best for operations on instances of the class。

 any objects。 static methods are best for general utility functions。

 which do not need access to class data。

![](img/5bfb5bb56c14c748bea4c8745236b37a_49.png)

![](img/5bfb5bb56c14c748bea4c8745236b37a_50.png)

Class methods are best used when we're working with class level data。

 or we require access to the class itself， such as when we're working with class variables。

 rather than using self as the first parameter， we're going to use CLS， meaning class。



![](img/5bfb5bb56c14c748bea4c8745236b37a_52.png)

![](img/5bfb5bb56c14c748bea4c8745236b37a_53.png)

And well everybody， those are class methods in Python。



![](img/5bfb5bb56c14c748bea4c8745236b37a_55.png)
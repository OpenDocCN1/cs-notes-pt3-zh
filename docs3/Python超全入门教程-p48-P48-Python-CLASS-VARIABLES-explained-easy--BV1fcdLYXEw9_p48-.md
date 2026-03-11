# Python超全入门教程-p48-P48-Python-CLASS-VARIABLES-explained-easy--BV1fcdLYXEw9_p48-

Hey everybody， Today， I got to talk about class variables in Python。

 Class variables are shared among all instances， meaning objects created from a class。

 Instance variables are defined inside of the constructor。

 class variables are defined outside of the constructor with class variables。

 They allow you to share data among all objects created from the class with instance variables。

 Each objects has their own version with a class variable All those objects share one variable。

 Here's an example。 We will create a class of student。



![](img/3755ff6b38dda80c5dd364d2e78c0bf6_1.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_2.png)

We also need a constructor。When we create a student object。

 this constructor is automatically going to be called， but we need to pass in some arguments。

 We are provided with self。 Se refers to the object we're currently working with。

 We will set up a name parameter， and an age parameter。

We will assign self the object we're currently working with。

Set the name attribute to equal the data for the name that we receive from this parameter。



![](img/3755ff6b38dda80c5dd364d2e78c0bf6_4.png)

And self dot age equals age。Let's construct two student objects。 We will have student one equals。

 then called the constructor for student。So type the name of the class。

 followed by a set of parentheses to invoke it。 This will automatically call the constructor。

 but we have to pass in data for the name and the age for the name。 Let's pass in Sponongebob。

 because basically， everybody in the world knows who Spongebob is。

 I don't know how old Sponongebob is will say he's 30。



![](img/3755ff6b38dda80c5dd364d2e78c0bf6_6.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_7.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_8.png)

We'll create another student object， which we will refer to as student 2。

 We will call the constructor。

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_10.png)

Of our student class， pass and data for the name and age。Student 2 will be Patrick。

 Patrick will be 35。Okay， let's make sure this works。Let's print。Student one。Name。

Followed by student one's age。

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_12.png)

And we should get Sponongebob and as age as 30。 Let's print student whose's name and student whose's age。

Patrick， Patrick is 35。 Now， we'll create a class variable。

 Class variables are defined outside the constructor。

 and they are shared among all objects created from that class。

 Each object has their own name and age property。 These are instance variables。

 but class variables are defined outside the constructor。 Each object will share this one variable。



![](img/3755ff6b38dda80c5dd364d2e78c0bf6_14.png)

So if we're working with students。Let's say there is a class variable。Of class year。

 what is the graduating year of this class。

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_16.png)

2024。Now， let's print student ones graduating year。



![](img/3755ff6b38dda80c5dd364d2e78c0bf6_18.png)

Print student 1。Dot class。Ye。Okay， so Sponongebob has a class year of 2024。

 that's when he's graduating。Let's check student2。Patrick， his age is 35。

 his graduating class year is 2024。

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_20.png)

Now， with class variables， you can access them through any one object。

 such as student 1 or student 2。 It's good practice to access a class variable by the name of the class。

 rather than any object created from the class。 Since we're accessing class year。

 we'll access this class variable by the name of the class of student。



![](img/3755ff6b38dda80c5dd364d2e78c0bf6_22.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_23.png)

Make sure the S is capital。This helps with clarity and readability。

 If I was looking at this print statement， I can tell that class year is a class variable because we're accessing it directly from the class。

In not any instance from this class， without looking at this class。

 I can't tell if class year is an instance variable or a class variable。

 But if I access it via the class name， it's more explicit。

 So it's good practice to access a class variable by the class name itself。

 in not any one instance of this class。

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_25.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_26.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_27.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_28.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_29.png)

Let's create another class variable。We'll create a class variable to keep track of how many students we have created。

 this class variable will be nu students， meaning number of students equals0。



![](img/3755ff6b38dda80c5dd364d2e78c0bf6_31.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_32.png)

So within our constructor， we can write any code that we want。

 This code will always be executed when we instantiate an object。

I would like to take our number of students and increment it by one each time we construct a new student object。

So instead of using self， self refers to the object we're currently working with。

 if we're constructing student1， just imagine we're replacing self with student 1 or student 2 if we were constructing student2。



![](img/3755ff6b38dda80c5dd364d2e78c0bf6_34.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_35.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_36.png)

If we're going to be modifying a class variable。In place of self。

 we'll use the name of the class student。Access our class of student。

 Get the class variable of number of students。Then I will increment it by one。Plus， equals  one。



![](img/3755ff6b38dda80c5dd364d2e78c0bf6_38.png)

We are constructing two student objects。I will print。Access our class of student。

Get the number of students and print it。 We're constructing two student objects。

 If I print the number of students that we have， it should be two。

 then just to be sure that this is working， let's construct a third student object。

 Student 3 equals student。

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_40.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_41.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_42.png)

This student will have a name of Squiidward。 Squiidward's age will be 55。Now we have three students。

And for good measure， let's construct one more。Student 4 equals。 We will create a new student。

With a name of Sandy， Sandy's age will be 27。The number of students is now 4。



![](img/3755ff6b38dda80c5dd364d2e78c0bf6_44.png)

Just as an exercise。Using enough string， let's print the student classes class year as well as the number of students。



![](img/3755ff6b38dda80c5dd364d2e78c0bf6_46.png)

I will print。 Use enough string。My graduating。Class。Of， let's add a placeholder。



![](img/3755ff6b38dda80c5dd364d2e78c0bf6_48.png)

Access the class of student。Then， access the class year。My graduating class of 2024。Has。

 then we need the number of students will add a placeholder。Access the class of student。

Access the number of students。Has blank。Students。Let's see if this works。

My graduating class of 2024 has four students。 Now， if I were to change 2024 to 2025。

 my graduating class of 2025 has four students。

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_50.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_51.png)

Let's print the name of each student。These are instance variables。 Student1 dot name。



![](img/3755ff6b38dda80c5dd364d2e78c0bf6_53.png)

Then we need student two， three， and 4。

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_55.png)

My graduating class of 2025 has four students， Sponongboob Patrick Squiidward Sandy。



![](img/3755ff6b38dda80c5dd364d2e78c0bf6_57.png)

All right， everybody。 So those are class variables。

 Class variables are shared among all instances of a class。

 They are defined outside of the constructor。 The benefit is that they allow you to share data among all objects created from that class。

 And well， everybody， those are class variables in Python。



![](img/3755ff6b38dda80c5dd364d2e78c0bf6_59.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_60.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_61.png)

![](img/3755ff6b38dda80c5dd364d2e78c0bf6_62.png)
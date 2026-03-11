# Python超全入门教程-p57-P57-Learn-Python-NESTED-CLASSES-in-9-minutes--BV1fcdLYXEw9_p57-

Hey， what's going on， everybody。 So in today's video， I got to talk about nested classes in Python。

 A nested class is a class defined inside of another class。 This has a few benefits。

 We can logically group classes that are closely related。

 We can encapsulate private details that aren't relevant outside of the outer class。 And also。

 it helps keep our namespace clean。 It reduces the possibility of naming conflicts。 So， for example。

 let's say we have two classes， both named employee。😊，Within this class。

 I'm just going to print something。This is the first class。Then let's copy our employee class。

 paste it again。

![](img/9e9b040187b388b4c9a73869056ddbef_1.png)

This is the second class。We have a naming conflict。 We have two classes with the same name。

 If I were to run this program。

![](img/9e9b040187b388b4c9a73869056ddbef_3.png)

We will execute both。 This is the first class。 This is the second class。

 It is fairly noticeable that we have two classes with the same name。But with Python。

 we do a lot of importing and exporting of large files。 We may not realize there's a name conflict。

 One concept that'll help us avoid naming conflicts is the use of nested classes。

 Let's say we have employees for a company and another set of employees for a nonprofit organization。



![](img/9e9b040187b388b4c9a73869056ddbef_5.png)

![](img/9e9b040187b388b4c9a73869056ddbef_6.png)

I could write something like this。

![](img/9e9b040187b388b4c9a73869056ddbef_8.png)

We'll create a class。Of company。Within this class of company。

 we will have an inner class of employee。

![](img/9e9b040187b388b4c9a73869056ddbef_10.png)

With our second employee class， we will create an outer class of nonprofit。This is perfectly fine。

 We can have two classes with the same name as long as they're within different scopes。

These two employee classes might have different attributes， depending on who they work for。

 If they work for a company， they might have one set of attributes。 if they work for a nonprofit。

 they might have a different set of attributes。 So by using nested classes。

 this helps keep the namespace clean。 We can reuse this employee class because they have different scopes。

 Now， what we're going to do in this example。

![](img/9e9b040187b388b4c9a73869056ddbef_12.png)

![](img/9e9b040187b388b4c9a73869056ddbef_13.png)

![](img/9e9b040187b388b4c9a73869056ddbef_14.png)

What we'll do in this example is create some employee objects that belong to a company object as a placeholder for now。

 I'll write pass within the employee class。

![](img/9e9b040187b388b4c9a73869056ddbef_16.png)

![](img/9e9b040187b388b4c9a73869056ddbef_17.png)

With our class of company， let's define a constructor。 Do pay attention to the indentation。

 We are within the company class， but not the employee class。 This constructor is for the company。

 the company object we're going to create。

![](img/9e9b040187b388b4c9a73869056ddbef_19.png)

If we construct a company object， we need a company name such as the Crty crab。



![](img/9e9b040187b388b4c9a73869056ddbef_21.png)

I will assign self dot company name。Equals the company name that we receive。



![](img/9e9b040187b388b4c9a73869056ddbef_23.png)

We are also going to declare an attribute of employees。This attribute will be an empty list。

 We will append employee objects to our list of employees。Then we will create a method to add。

Employee。We will need a name， meaning name of the employee and a position。 What's their job。For now。

 I'll write pass。 We'll get back to this later。And I will define a method。Of list。Employees。

And again， I'll write pass。

![](img/9e9b040187b388b4c9a73869056ddbef_25.png)

Okay， let's be sure that our company name works。

![](img/9e9b040187b388b4c9a73869056ddbef_27.png)

I'm going to create a company object， company。

![](img/9e9b040187b388b4c9a73869056ddbef_29.png)

Equals company， but I have to pass in a company name。I will pick the crusty crab。

Then just to be sure that this works， I will display our companies。Company name， attribute。



![](img/9e9b040187b388b4c9a73869056ddbef_31.png)

That would give me the crusty crab。

![](img/9e9b040187b388b4c9a73869056ddbef_33.png)

So we know that that works。Within our employee class， let's define a construct。 Def， init。

We need a name。And a position。Self dot name equals name。Self dot position。



![](img/9e9b040187b388b4c9a73869056ddbef_35.png)

Equals position。Let's create one more method of define。Get。Details。



![](img/9e9b040187b388b4c9a73869056ddbef_37.png)

We will return the details of an employee。 All we're going to do is return enough string。

Add to placeholders。We will return self dot name。And a self dot position。



![](img/9e9b040187b388b4c9a73869056ddbef_39.png)

All right， now within our a employee method。We will construct a new。Employee object。



![](img/9e9b040187b388b4c9a73869056ddbef_41.png)

Equals now if we're going to access this inner class of employee。



![](img/9e9b040187b388b4c9a73869056ddbef_43.png)

We're going to prefix self。Self meaning this company object that we're currently working with。



![](img/9e9b040187b388b4c9a73869056ddbef_45.png)

We need the class of employee， Then we'll call the constructor。

 but we have to pass in a name and a position when we receive a name and a position。



![](img/9e9b040187b388b4c9a73869056ddbef_47.png)

![](img/9e9b040187b388b4c9a73869056ddbef_48.png)

We will pass that to the employee Conor。

![](img/9e9b040187b388b4c9a73869056ddbef_50.png)

Once we have our new employee object， we're going to take our list of employees。



![](img/9e9b040187b388b4c9a73869056ddbef_52.png)

Self do employees。

![](img/9e9b040187b388b4c9a73869056ddbef_54.png)

Use the append method of lists。Then add our object of new employee to the empty list。



![](img/9e9b040187b388b4c9a73869056ddbef_56.png)

Let's create a few employee objects。 We'll take our company。

 use the Add employee method that we have created。We need a name and a position。

I will pick Eugene for Eugene crabs。His position is that he is the manager。Let's create two more。

Take our company object。Use the addd employee method that we have defined。

I will pass in a name of this employee asked Spongeebob， his position is that he is a cook。

Then we have Sid word。Company do add。Employee method。First name， Squiidward。

His position is that he is a cashier。

![](img/9e9b040187b388b4c9a73869056ddbef_58.png)

So this should run with no problems。Now I would like to list all of the employees at this company。



![](img/9e9b040187b388b4c9a73869056ddbef_60.png)

We'll need to rely on this get details method。So when we list our employees。

We will return a list comprehension。For every employee。In self dot employees。This is an attribute。

 It's a list of employee objects。 It is iterable。Take each employee。That we're iterating through。

Call the get。Details method， and return it。

![](img/9e9b040187b388b4c9a73869056ddbef_62.png)

Now， if I was to take my company， then call the list employees method。Whoops， I forgot to print it。

We will print each employee's name and their position。However。

 I think this would look better if we were to use a for loop。For every。Employee。In。Take our company。

Call the listEmploy method。During each iteration。We will print each employee。



![](img/9e9b040187b388b4c9a73869056ddbef_64.png)

![](img/9e9b040187b388b4c9a73869056ddbef_65.png)

We have Eugene， that's Mr。 Krabs， the manager， Spongeebob， the Cook， and Squiidward the cashier。



![](img/9e9b040187b388b4c9a73869056ddbef_67.png)

![](img/9e9b040187b388b4c9a73869056ddbef_68.png)

To demonstrate the reusability of classes， let's create a second company object that has its own employees。



![](img/9e9b040187b388b4c9a73869056ddbef_70.png)

Let's rename company as Company1。Then we will create company2。



![](img/9e9b040187b388b4c9a73869056ddbef_72.png)

Company 2 equals called the company constructor。 My second company will be the chum bucket。

We'll take company2， then add to employees， Company2 do add。Employee。We will pick Sheldon。

Sheldon is the manager。Company 2。Dot add。Employee。Karen will be the assistant。



![](img/9e9b040187b388b4c9a73869056ddbef_74.png)

For every employee in company， too， list the employees during each iteration。

 print the current employee。

![](img/9e9b040187b388b4c9a73869056ddbef_76.png)

We have Sheldon。 That's plankton's first name。 He's the manager， and Karen is his assistant。



![](img/9e9b040187b388b4c9a73869056ddbef_78.png)

Art everybody。 So those are nested classes。 It's a class defined inside of another class。

 You have an inner class and an outer class。 A few of the benefits is that we can logically group classes that are closely related。

 such as having employee objects within a company object。

 We can encapsulate private details that aren't relevant outside of the other class。

 We may have no need to create employee objects outside of this class。 and by using nested classes。

 It helps keep the namespace clean。 It reduces the possibility of naming conflicts。

 with another type of organization。 We could create another inner employee class。 And well。

 everybody， those are nested classes and Python。😊。

![](img/9e9b040187b388b4c9a73869056ddbef_80.png)

![](img/9e9b040187b388b4c9a73869056ddbef_81.png)

![](img/9e9b040187b388b4c9a73869056ddbef_82.png)

![](img/9e9b040187b388b4c9a73869056ddbef_83.png)
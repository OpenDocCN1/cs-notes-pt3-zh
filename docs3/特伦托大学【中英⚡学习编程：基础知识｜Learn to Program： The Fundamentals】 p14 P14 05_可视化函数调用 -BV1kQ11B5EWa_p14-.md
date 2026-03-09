# 特伦托大学【中英⚡学习编程：基础知识｜Learn to Program： The Fundamentals】 p14 P14 05_可视化函数调用 -BV1kQ11B5EWa_p14-

In this video， we're going to use the Python visualualizer to explore how function calls are managed in computer memory。

We have written a function called convertt to Minute。

 which takes in a number of hours and returns the equivalent number of minutes。



![](img/3acb9c836d4298a4fc2da5790e4b435f_1.png)

For example， if we call convert to minutes with argument 2， then we expect to get back 120。

Because there were 120 minutes in two hours。Notice the indentation。

 all code belonging to a function must be indent， typically four spaces。



![](img/3acb9c836d4298a4fc2da5790e4b435f_3.png)

Let's visualize what happens when we run this program。

When we read the function definition or rather when Python die。

We see that a variable call convert to minutes is created。



![](img/3acb9c836d4298a4fc2da5790e4b435f_5.png)

It contains the memory address of a function object。

 That function object contains all information about the function。

 including any code that needs to be executed， the parameter。



![](img/3acb9c836d4298a4fc2da5790e4b435f_7.png)

![](img/3acb9c836d4298a4fc2da5790e4b435f_8.png)

![](img/3acb9c836d4298a4fc2da5790e4b435f_9.png)

And the dostream。We are now paused on line  pen0， which contains an assignment statement。

Notice the variable minutes too has not been created yet。

That will happen after we finish executing the assignment statement。



![](img/3acb9c836d4298a4fc2da5790e4b435f_11.png)

So first we have to evaluate the expression on the right hand side of the equal symbol。

 and that expression is a function call。Once that function call has returned。

 it will give us back a value and minutes， too， will be created。

 and it will store the memory address of that returned value。



![](img/3acb9c836d4298a4fc2da5790e4b435f_13.png)

In order to execute this function call， the argument is evaluated。



![](img/3acb9c836d4298a4fc2da5790e4b435f_15.png)

![](img/3acb9c836d4298a4fc2da5790e4b435f_16.png)

That will create a box for value2。 In addition， a new region of memory will be created to keep track of what happens while convert to minutes is executed。



![](img/3acb9c836d4298a4fc2da5790e4b435f_18.png)

Here is value2。

![](img/3acb9c836d4298a4fc2da5790e4b435f_20.png)

And here is variable nu matter。The area of computer memory to the right is called the HeEap and contains all the values that are created during execution of a program。



![](img/3acb9c836d4298a4fc2da5790e4b435f_22.png)

The area of memory to the left is called the call stack。

 it's called a stack because it's like a stack of plates when a function is called a stack frame is created and when that function returns。

 its frame is removed from the stack and control passes back to the collar of that function。



![](img/3acb9c836d4298a4fc2da5790e4b435f_24.png)

Each frame contains variables that are specific to that section of the program。

The main frame contains variables that are created outside of any function。

 and frames for functions contain parameters and local variables。

A local variable is any variable that is created inside of a function such as variable result。



![](img/3acb9c836d4298a4fc2da5790e4b435f_26.png)

![](img/3acb9c836d4298a4fc2da5790e4b435f_27.png)

Line7 contains an assignment statement。We evaluate the right hand side。

 We look up what numb hours is， and it's22 times 60 is 120。 so we're going to see。

A value 120 get created， and we're going to see a variable result get created inside function convert to minutes。

Result refers to 120。 No hours refers to 2。

![](img/3acb9c836d4298a4fc2da5790e4b435f_29.png)

We're about to execute a return sleep。That's going to evaluate result， which is 120。

 and it's going to yield that memory address。

![](img/3acb9c836d4298a4fc2da5790e4b435f_31.png)

Notice that we get to see what the return value is。As soon as we click forward one more time。

We're going to exit function convert to minutes。Control is going to pass back to where we were in the program。



![](img/3acb9c836d4298a4fc2da5790e4b435f_33.png)

That was right here。 we're going to finish this call to convert to minutes with argument two and it's going to give us back the memory address of value 120。

That should。Create a variable minutes too。

![](img/3acb9c836d4298a4fc2da5790e4b435f_35.png)

Indeed， that's what happened。The stack frame for the call to convert to minutes is gone。

Going from computer memory， that's what happens when a function exits。

We're going to step through another call and convert to minutes。

 This time we're going to pass in argument 3， and we're going to save the results。

 store the result in minutes 3 here。 Let's watch that happen。 We evaluate 3。

 which creates it in the heap。

![](img/3acb9c836d4298a4fc2da5790e4b435f_37.png)

![](img/3acb9c836d4298a4fc2da5790e4b435f_38.png)

![](img/3acb9c836d4298a4fc2da5790e4b435f_39.png)

![](img/3acb9c836d4298a4fc2da5790e4b435f_40.png)

None hours refers to that value。 Now， it used to refer on the first call to value 2。 Now。

 it refers to value 3， because we've called it with a different argument。Now。

 when I calculate numb hours time 60， I look at the stack here。

 and I see that I'm taking three times 60。 That's 180。

 And so we're going to get a variable result referring to 180， we still have。



![](img/3acb9c836d4298a4fc2da5790e4b435f_42.png)

![](img/3acb9c836d4298a4fc2da5790e4b435f_43.png)

Value 120 up here， because outside， outside of this function， minutes， too still refers to it。

Now we're going to return。18。That will yield memory address ID5。

 which is going to be stored inside new variable Min 3， which will be created in this main module。



![](img/3acb9c836d4298a4fc2da5790e4b435f_45.png)
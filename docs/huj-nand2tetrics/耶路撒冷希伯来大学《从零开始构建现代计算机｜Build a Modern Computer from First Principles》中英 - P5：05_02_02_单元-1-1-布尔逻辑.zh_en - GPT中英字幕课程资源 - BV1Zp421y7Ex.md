# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P5：05_02_02_单元-1-1-布尔逻辑.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/0a89ff649e99c24f50f2bfc4a8ed8675_0.png)

So today， we're starting our journey of actually building a computer。

 You've probably all heard that computers internally only have zeros and ones。

 And the reason that they only have zeros and ones is because that's what they can get away with。

 It's simplest to have only two possible values that you need to maintain。

 And that's going to be enough， as we will see today。

We're starting with actually the completely theoretical logical kind of analysis of how to deal with zeros and ones。

 and later this later in unit 3， we'll actually talk about how these abstract0 in one signals directly are implemented as chips inside a computer。

So let's talk about the abstract0 in one， on and off to or false， not no and yes，0 in one。

 in general， we can use all these names to refer to each one of two different physical values that are maintained somewhere in the system。

 We will use0 in one for the rest the rest of this unit， but that's completely general。

So what can we do with kind if we only have zeros in ones， Well。

 we can do some kind of basic operations on them。 For example， the and operation takes 20。

1 signals and returns one。 only if both of them were one。 So if you have 0 and one， the result is 0。

 But if you have one in one， the result is one。We can actually see all the different possibilities for combining two values of zeros and ones into a result。

 which is the end of them in a little table that is called the true table because it actually gives all the different possibilities of the inputs of x and of y。

 and for each one of these possibilities， it lists what is the output， what is x and y。😊。

So and is one of the possible operations。 Here's another very popular one。 Or it returns one。

 If any one of the two inputs is true is one。Or even if both of them are one。

 the only time to return to 0 is if both x and y are 0。And here's a third interesting operation。

 This one is a unary operation。 It only takes a single input bit as input X and returns the opposite of it。

 So return for if the input is0， the output is one。 If the input is one， the output is 0。

 So these are possible， very simple operations and Boolean numbers。

 sort of like addition and multiplication and maybe other kind of operations。

 our operations on integers or in real numbers， These are operations and Boolean numbers。😊。

Once we have operations， we can start combining them just like we combine arithmetic operations in arithmetic formulas。

 So， for example， let us try to evaluate what would be the expression of not0 or one and one。

 noticeice that we have parenthses to give us a priority here。 So the way we evaluate it。

 It's very simple。 We know how to evaluate one and one， which is one。

 So the whole thing simplifies to not0 in one or one。 We know how to evaluate 0 or one。

 that's going to be one because it's an or operation So that's equal to not one。

 And now we know how to evaluate not one。 that's simply0。 all very simple and we can do that。😊，Now。

 once we know how to evaluate Boolean expressions over values over01 values。

 then we can actually get general expressions， general functions that takes indeterminants X， Y。

 z as inputs。 and for each value of X， Y Z produce an output。 So for example。

 I can define a function a function of three inputs， X， Y and z， that basically tend X and y。

 or not X and z， and look into the parentheses to seize the priorities that I was thinking about。

 Of course I could use， I could define any other function by any other Boolean formula and that would give me a function。

😊，If we want to know what kind of function is that， well。

 we can actually list all the possible value of the X， Y， and Z。 And for each one of them。

 try to write down what is the value of the function。😊。

The really nice thing about Boolean values is the fact that there are only a finite number of possible inputs。

 and we can actually list each one of them。 This is completely different from functions that you've learned in third grade where you have functions from integers to integers。

 and there are infinitely many integers。 so you can never write down the function in a complete specification of all the possible values。

 But here we can actually write down all the possible values that x is a tricklet。 X， Y， Z can have。

 We can have x 0， Y 0 and z 0 that corresponds to the first row in the table。 and so on。

 until the last row of the table that corresponds to all three of them being one。😊，Now。

 for each one of these rows， we can just evaluate the function， what is as a function F of x。

 Y z defined by the previous formula for these values。 For example。

 let's look at the second row in the second row we have x equals 0。

 y equals0 z equals1 and we can just plug in the numbers 0。

01 into the formula every time we have an x we put a zero there every time we have a y we put a zero there every time we have a z。

 we put the ones there and now we just get formula with constants in it and we can evaluate it just like we did in the previous slide and we can figure out that that is one that the second row should get the value of one we can do this similarly for each one of the possible rows and we get we can completely fills the table and now notice that this table a values completely gives you is the same information as the previous expression did it completely specify the function。

 the boolean function that we just had。😊，The first first way we describe the function was as a formula。

 The second way we describe the function was as a true table。

 and these are two completely identical definitions， ways to describe the same Boolean function。

So now， once we know we can describe Boolean functions using formulas。

 and we basically we have general Boolean expressions。

 we can actually try to find what are a bunch of boolean identities that always give us equality。

 For example， we can always see that x and Y， whatever is the values of x and Y is。

 is exactly equal to y and X。 This is called the commutative law。

 We have the same similar phenomena for x or y equals y or X。😊。

So these are like commutative laws that hold for these Boolean algebra in this Boolean algebra。

There are a bunch of other kind of identities。 For example， use use the wellknow associative law。

 If you have X and y and Z， it's the same thing if you first do X and Y or whether you first do Y and Z。

 similar thing happens for or， another when known law is a distributive law。

 If you have X and Y or Z， that turns out to be exactly equal to X and Y， all that or X and Z。Now。

 as opposed to the usual arithmetic where we only have a distributive law of multiplication over addition here we have both the distributive law of of and over or and the dual law of distributive law of O or over n。

 The same trick works if you want to do X or， Y and Z。 That's X or Y and X or Z。Now。

 there are also a laws called the Morgan laws that govern how knots work。

 how they interrelate with and and ore。 These are called laws are called de Morgan laws。

 And they say the following to interesting thing。 If you take X and Y and do a n and all of that。

That's equivalent to first doing n of x and oing that to n of y。

And we have the dual one that if you have not of X or Y。

 that's exactly equal to not of X and not of y。 Now， all these laws can be easily proved。

 if you wish， not if you wish， really proved by simply listing all the possibilities in a true stable and verifying that they get the same true table for the left hand side and the right hand side。

😊，Now， there are a bunch of other laws， and we can use them to actually do manipulations on Boolean algebra。

 So， for example， once we have a formula。 for example， the formulas that you see here。

 not of not X and not X or Y。 for example， it could be any other formula。

 We can now start applying some of these identities to change its form to simplify it or to just bring it into a different format。

 So for example， the first thing we can do here is look at the second part is's the last sub expressionpress。

 the not x or Y。 we can use the Morgan law here and basically convert it to not X and not Y。😊，Now。

 if you look what we have here， we can use the associative law because we have not X and。

 not X and not Y。 We can change the order of doing the end。And we get another expression。

 which is identical using the associative law。 At this point。

 we have something really interesting in the beginning。 We have not X and not x。

That can be just simplified to not X。 Why is that， Because we can know we can actually see also that's another identity that we didn't explicitly list。

 but it's easy to verify in the same way that if you take any value。 W， In our case。

 W is not X and do W and W， that's completely equivalent to W。😊，Now。

 this is called the idpotence law， and we can thus simplify the previous expression by simply removing one of these ws。

 one of these not X's。Now we are ready to use the Morgan loggon。And now we got into not。

 not X or not， not Y。 Now， again， here's another law that we didn't list explicitly。

 but you obviously all know that not not x is always equal to x。 So using double negation law。

 we can simplify that to x or y。So that just gives you some kind of demonstration that you can basically just manipulate bullolean expressions。

 sort of like you manipulate arithmetic expressions in elementary school。

There's another way to get the same conclusion， the same equivalentence without actually going through these algebraic manipulations。

 simply by actually looking at the truth table。 We take the expression。 We build a true table for it。

 and we've already seen how to take an expression and find its true table。

 And then we get the true table that you see on the board。😊，Now， once you have this truth table。

 you can say， I know this truth table。 This is exactly the truth table of the or function。

 And then that immediately proves that the expression on the top is completely equivalent to X or Y。

 as we've derived using algebraic methods previously。😊，Now， of course， it's not completely。

 You won't always be so lucky to do some kind of big truth table and recognize what it is and immediately see a better and nicer and simpler expression It gives you the same table。

😊，Sometimes you will have to do algebraic manipulations。 But on the other hand。

 it's not always true that algebraic manipulations are easy to do。

 And the sense of finding a very simple expression。 So， but in general， in principle。

 you can use both of these methods to actually simplify Boolean expressions or find alternative forms that give you the same Boolean expression。

So we've just finished our first unit describing how to how to manipulate logical values。

 Notice that we're still keeping our abstract point of view of just logical values and not thinking about any physical realization that we will have inside our computer。

And the third unit will actually switch our point of view and start talking about the same kind of phenomena。

 But from the point of view of real chips and real gates that we have inside a computer。

 But we forget to that in the next unit， we'll keep maintaining。

Our theoretical point of view and start talking about the following problem。

 How can we construct a function from basic operations， How does that。

 This is exactly the kind of things we will need to do when constructing hardware。

 We know what it wants to do， but we will have to actually construct it from Booleion operations and we'll try to see how that is done first。

 from a theoretical point of view in the next unit。



![](img/0a89ff649e99c24f50f2bfc4a8ed8675_2.png)
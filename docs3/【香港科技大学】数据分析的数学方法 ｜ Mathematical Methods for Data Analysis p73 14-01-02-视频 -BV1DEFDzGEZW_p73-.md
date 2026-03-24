# 【香港科技大学】数据分析的数学方法 ｜ Mathematical Methods for Data Analysis p73 14-01-02-视频 -BV1DEFDzGEZW_p73-

We go to a case study of the linear approximation and differentiation。



![](img/32705b42755083dc6c186975cdead1fa_1.png)

We will study how to use linear approximation and differentiation to solve optimization problems。

How to use differentiation and linear approximation to set up a theoretical foundation of optimization。

How to use them to develop algorithms for optimization。Oimization。And对。Griient。Descent。

we have mentioned in the very early of this course。

Optimization is one of the key elements in machine learning。

 Mach learning equals representation plus evaluation plus optimization。

Most of the machine learning task will be solved eventually by optimization。In this section。

 we consider the so called unconstrained optimization。Minimization of F of X， X on V。Where。

V is a hereable space。We will call this problem， O P T problem。In this optimization problem。

 we have a function F of x for this F， we don't have any constraint on x。 X can be any vector in V。



![](img/32705b42755083dc6c186975cdead1fa_3.png)

Therefore， we call this optimization an unconstrained optimization。



![](img/32705b42755083dc6c186975cdead1fa_5.png)

To start with。We discuss。The solvability and Opity。

We will discuss whether or not this problem is solvable。If it is solvable。

How to characterize the solution of this minimization。Let's start with this solid。

Of the optimization problem， O， P T。We need first define what is a solution to this minimization。

We say X star is。A solutionution。Of this optimization problem。If。

F X star has the minimum value among all。Vctorors U。



![](img/32705b42755083dc6c186975cdead1fa_7.png)

We want F x star smaller than all equals to F of X。 X is even B。This condition is called a zeros。

Optimity condition。Because we use the only function values here。

 function value is the zeros derivative。

![](img/32705b42755083dc6c186975cdead1fa_9.png)

That's why this is called a zero Opity condition。

![](img/32705b42755083dc6c186975cdead1fa_11.png)

We wanted to find an X star such that FX star is smaller than all other Fx。

This exterior star is also called a minimizer。Or global minimizer。We call。Make the star。

 a global minimizer。

![](img/32705b42755083dc6c186975cdead1fa_13.png)

Of F。Denoted by。Argumy。Of F of X， X U V。X star is the argument of F of X。

 I have used this notation before。X star is an argument of F just means that F X star is smaller than F of X for all X U V。



![](img/32705b42755083dc6c186975cdead1fa_15.png)

Though we have defined the solution of this optimization problem。

 we don't know whether or not it exists。Now， we discuss the existence。Actually。

 the existence of the solution of this optimization is not guaranteed automatically。



![](img/32705b42755083dc6c186975cdead1fa_17.png)

We have many different cases。In the following， I just gave you several examples where the solution of optimization might not exist。



![](img/32705b42755083dc6c186975cdead1fa_19.png)

The first example is a polynoial。In R， F is from R to R。

And this F X is just X times x minus-1 times x plus 1。



![](img/32705b42755083dc6c186975cdead1fa_21.png)

It is a polynomial。The graph of this function。Is it has three roots，0，1 and minus-1。

It's a polynomial of degree 3。 The graph looks like。When this x goes to minus infinity。

This function value goes to minus infinity。

![](img/32705b42755083dc6c186975cdead1fa_23.png)

X goes to minus infinity。Function value， F。X goes to minus infinity。



![](img/32705b42755083dc6c186975cdead1fa_25.png)

Therefore， we cannot find an X star such that F X star is smaller than all F of x because for any given。



![](img/32705b42755083dc6c186975cdead1fa_27.png)

X， this Fx is just finite。If you claim that X star is a solution， then this FX star is always finite。

 but this F X can goes to minus infinity。

![](img/32705b42755083dc6c186975cdead1fa_29.png)

So it's a contradiction。

![](img/32705b42755083dc6c186975cdead1fa_31.png)

In the second example， I consider a function F from B to R， where V is a huber space。

 and this F X is a linear function A X。For some。A in V。This is an linear function。

 We know that for linear function。The function value at 0 must be 0。If v equals to R。

And if a is positive， then the graph of this Fx looks like。Then in this case。

When x goes to minus infinity， F x again goes to minus infinity so that there is no minimizer。

 there is no solution of the minimization of F of x。



![](img/32705b42755083dc6c186975cdead1fa_33.png)

In the general case， I can take。X equals c times a where C is just a real number。Then， F of x。Is AC。

 A， which is C times the a norm squared。You find that。This C goes to minus infinity。Again。

 you can see Fx。Goes to minus infinity。 if this a is not 0。So that as long as a is a non zero vector。

 this linear function will not have a minimizer。

![](img/32705b42755083dc6c186975cdead1fa_35.png)

The third example。In these two examples。The minimizer does not exist just because the function value can goes to minus infinity。



![](img/32705b42755083dc6c186975cdead1fa_37.png)

In the last example。This function value does not goes to minus infinity， but a finite number。

Even this F take a finite number， the minimizer also does not exist。Consider F is from R to R。

And we take F x equals1 over x for x larger than 0。Then the function looks like。

You can see this function value approaches 0。It can be very， very close to 0， but it is never0。

Which means that if I take a finite x， then this number is just non 0。

 I can always find a bigger x such that this F X is smaller， closer to 0。



![](img/32705b42755083dc6c186975cdead1fa_39.png)

![](img/32705b42755083dc6c186975cdead1fa_40.png)

There are many， many such examples。Where the。

![](img/32705b42755083dc6c186975cdead1fa_42.png)

Solution of optimization problem does not exist。So we should be careful when we want to solve a minimization problem。

The very first step for solving a minimization problem is to check whether or not that minimization has a solution。

We will discuss the existence of the solution later。



![](img/32705b42755083dc6c186975cdead1fa_44.png)
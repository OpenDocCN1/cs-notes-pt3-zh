# Python超全入门教程-p54-P54-Learn-Python-DUCK-TYPING-in-4-minutes--BV1fcdLYXEw9_p54-

Hey， everybody。 So today， I got to talk about duck typing in Python。

 Duck typing is another way to achieve polymorphism。 Besides using inheritance。

 Obs can be treated as if they're a different type。

 as long as they meet the minimum necessary attributes and methods required of them。

 It follows this adage。 If it looks like a duck and quacks like a duck。 It must be a duck。



![](img/fd124d4f4fdba10a181c73ffd5d33915_1.png)

![](img/fd124d4f4fdba10a181c73ffd5d33915_2.png)

![](img/fd124d4f4fdba10a181c73ffd5d33915_3.png)

![](img/fd124d4f4fdba10a181c73ffd5d33915_4.png)

As long as an object resembles another， it could also be treated of that type。 So in this example。

 let's create a class of animal。We will have a class attribute of a， if you're an animal。

You will have an attribute of alive。 You're a living creature。Let's create a class of dog。

The dog class will inherit from the animal class。They will inherit the alive attribute。

Let's also define a speak method。If you're a dog， you gain the ability to speak。 We will print。Wf。

Then we'll create a cat class。Class cat inherits from animal。For the Sp method， we will print Miao。

Let's create a list of animals。 What do these two classes have in common。

 They both could be considered animals。Let's create a list of animals。We will construct a dog object。

And a cat object。

![](img/fd124d4f4fdba10a181c73ffd5d33915_6.png)

If I was to write a for loop。For every animal in my list of animals。



![](img/fd124d4f4fdba10a181c73ffd5d33915_8.png)

Have each animal。

![](img/fd124d4f4fdba10a181c73ffd5d33915_10.png)

Use its speak method。Which will result in。The dog going Wof， the cat going Miow。

 They're both speaking。

![](img/fd124d4f4fdba10a181c73ffd5d33915_12.png)

What if we add a class that has nothing to do with animals？Like class car。

Cars will have a horn method。 That's how they speak。



![](img/fd124d4f4fdba10a181c73ffd5d33915_14.png)

When you honk the horn。You will print。

![](img/fd124d4f4fdba10a181c73ffd5d33915_16.png)

Hunk。Within my list of animals， let's create a car object。 It really doesn't belong in here。

 but let's see what happens。

![](img/fd124d4f4fdba10a181c73ffd5d33915_18.png)

We have an attribute error。 Car object has no attribute， speak。



![](img/fd124d4f4fdba10a181c73ffd5d33915_20.png)

Our car object doesn't have the minimum necessary attributes and methods。



![](img/fd124d4f4fdba10a181c73ffd5d33915_22.png)

When iterating through this list of animals， we're calling each animal speak method。

 which our car object doesn't have。 but it does have a horn method。

 So what if we rename our horn method， as speak， Maybe it's an AI car or something。



![](img/fd124d4f4fdba10a181c73ffd5d33915_24.png)

Well， this would work。 The dog goes whof。 The cat goes Miow。 The car goes hank。



![](img/fd124d4f4fdba10a181c73ffd5d33915_26.png)

![](img/fd124d4f4fdba10a181c73ffd5d33915_27.png)

So our car object。It quacks like a duck。 We could consider it a duck。

 It has the minimum necessary methods to be considered an animal。



![](img/fd124d4f4fdba10a181c73ffd5d33915_29.png)

![](img/fd124d4f4fdba10a181c73ffd5d33915_30.png)

Animals inherit this alive attribute。 Let's utilize that。After the animal speaks。

Let's print there a live attribute。Print my animals。 A live attribute。



![](img/fd124d4f4fdba10a181c73ffd5d33915_32.png)

My car object doesn't have that attribute。We get an attribute error。

 Car object has no attribute alive。

![](img/fd124d4f4fdba10a181c73ffd5d33915_34.png)

But if I was to add that attribute。

![](img/fd124d4f4fdba10a181c73ffd5d33915_36.png)

Alive equals false。

![](img/fd124d4f4fdba10a181c73ffd5d33915_38.png)

We have true for the dog。 It's living， Tru for the cat。 It's living， but false for the car。

 It's not living。 It's not a living creature。

![](img/fd124d4f4fdba10a181c73ffd5d33915_40.png)

![](img/fd124d4f4fdba10a181c73ffd5d33915_41.png)

My car meets the minimum necessary requirements to be considered an animal。

 If I were to set this to be alive。

![](img/fd124d4f4fdba10a181c73ffd5d33915_43.png)

![](img/fd124d4f4fdba10a181c73ffd5d33915_44.png)

Well， then it would be a living car。 kind of like the movie cars。So with Python。

 duck typing is another way to achieve polymorphism。 Besides using inheritance。

 as long as an object has the minimum necessary attributes and methods。

 you could treat it as a different type of object。 if it looks like a duck in quacks like a duck。

 It must be a duck。 And well， everybody， that is  duck typing in Python。



![](img/fd124d4f4fdba10a181c73ffd5d33915_46.png)

![](img/fd124d4f4fdba10a181c73ffd5d33915_47.png)
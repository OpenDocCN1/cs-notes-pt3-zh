# 【阿尔伯塔大学】问题解决Python编程和电子游戏 ｜ Problem Solving, Python Programming, and Video Games p38 05_01_01_solution-issues-in-hacking-version-2 -BV1N5rLBWE1c_p38-

![](img/6786fa7eedbeacccf86c97f03dca9c0f_0.png)

Let's explore solution improvements for the second version of hacking that we will include in the third version。

Visually， the game looks like the final version， but it is missing a lot of functionality。

 For example， there is only one path through the game。 no matter what password the player enters。

 a failure outcome message is displayed。We need a way to follow alternate paths in hacking。

 The game should select an outcome based on the password the player enters。

Comparing the player's guess to the correct password is a computation。

 Our algorithms and programs must be able to perform selection based on the results of computations。

😊，The language constructs that provide this ability are called control structures。

 A control structure dictates when an algorithm step or program statement is performed。

 including whether is performed at all。Version 3 of hacking will focus on the specific control structure called selection。

Introducing selection to your solution will result in changes to your description， test plan。

 algorithm， and code。By observing and playing version 3。

 you can identify the appropriate outcome based on whether a correct or incorrect answer is entered。

In this version， you will modify the description so that it reflects the different game outcomes。

This will involve a new kind of attribute called a selection attribute。

A selection attribute is a temporal attribute that is used as a response to a choice in the game。

 and will usually start with if。For example， now that the game compares correct and incorrect guesses to produce a specific outcome。

 you may use the selection attribute if the guess is incorrect to describe the object。

 the game displays a failure outcome。Whenever you use selection to create alternate paths in a game。

 you need to test each path。In the first test plan for hacking。

 you added tests to consider the two possible player actions。

 entering a correct password and entering an incorrect password。In version 1。

 there was only one path。No matter what guess the player entered， a failure message was displayed。

 Now that there are multiple paths in the game， you need to update your test plan to indicate that the player choice determines one of two possible outcomes。

Both of these outcomes must be tested in a separate programme run。

 Both the tests and implementations of these outcomes are independent cases。

 This is an example of a new problem decomposition technique called case based decomposition。

 where multiple independent solution parts are created separately and joined together to form a complete solution。

Observe hacking version 3 now so that you can create your version 3 description and test plan。



![](img/6786fa7eedbeacccf86c97f03dca9c0f_2.png)
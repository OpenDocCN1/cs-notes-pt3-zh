# 【阿尔伯塔大学】问题解决Python编程和电子游戏 ｜ Problem Solving, Python Programming, and Video Games p102 12_04_01_program-poke-the-dots-version-5 -BV1N5rLBWE1c_p102-

![](img/5e8668ffd57bfdc0a1547fa63481afe0_0.png)

As you program the final version of pokeke the dots， there are a few things to keep in mind。

To determine if the game is over， you must check if the dots intersect each other。

In the user defined methods less than， you saw an example of a method for a rectangle object that determines if two objects of that type intersect。

 but you will need a different computation for intersecting dots。

All points in a filled circle are less than or equal to a fixed distance from the center。

This distance is called the radius。 If two circles intersect。

 the distance between centers must be less than the sum of their radii。

You can use the distance formula to compute the distance between two points。

After you have determined that the game is over， you must draw the game over message。

 This message uses the colors of the two dots， but you already know that you cannot access the color attribute of a dot object directly。

To get this information， you must write a method in the dot class that returns its color。

Program the fifth and final version of Poke the dots now。



![](img/5e8668ffd57bfdc0a1547fa63481afe0_2.png)
# 【精译⚡算法导论】AbdulBari p18 p17 2 Divide And Conquer -BV1hhPXeTEWM_p18-

Hello， friends。 I am going to start an next topic in algorithms that is divide and conquer strategy。

 The first topic was analysis of algorithm。 In that topic。

 I have shown you how to write an algorithm and how to analyze an algorithm。

 and what is the purpose of analysis。Now， the next topic is divide and conquer。

This topic is related to a strategy for solving a problem。Like this。

 we have other strategies also in the subject like 3D method， dynamic programming， backtracking。

 branch and Bo， so this is one of the strategy。So let us understand what is a strategy。

Strategy is an approach or a design for solving a problem。For solving any problem。

 computational problem， you can adopt this strategy for solving the problem if the strategy is suitable for the problem。



![](img/f1beacab9bd12c8f2d11b482defbaec5_1.png)

So by practice， you can come to know there is no formula that this is the problem。

 this strategy is applicable。Though there are a few guidelines。

 so we can follow those guidelines and we can apply the strategy for solving a problem。



![](img/f1beacab9bd12c8f2d11b482defbaec5_3.png)

If a problem of some size is given， let us say size is n。



![](img/f1beacab9bd12c8f2d11b482defbaec5_5.png)

This sizes， size of the input for a problem。

![](img/f1beacab9bd12c8f2d11b482defbaec5_7.png)

So if a problem P is there of some size and if we say that this problem is large。

 then you can break this problem into smaller subproble。 P1， P2， P3。

 goes on as many problems as possible that depends on U。 So let us say K sub problems。



![](img/f1beacab9bd12c8f2d11b482defbaec5_9.png)

![](img/f1beacab9bd12c8f2d11b482defbaec5_10.png)

![](img/f1beacab9bd12c8f2d11b482defbaec5_11.png)

![](img/f1beacab9bd12c8f2d11b482defbaec5_12.png)

Now， the large problem is broken down into smaller subproble， so the size was larger。

 so we have broken to smaller size problems。

![](img/f1beacab9bd12c8f2d11b482defbaec5_14.png)

![](img/f1beacab9bd12c8f2d11b482defbaec5_15.png)

Now， these problems， some problems can be solved to obtain their solutions。 So for this solution 1。

 solution 2 and solution 3 and so on for this solution K。



![](img/f1beacab9bd12c8f2d11b482defbaec5_17.png)

![](img/f1beacab9bd12c8f2d11b482defbaec5_18.png)

All these are individually solved。Now， once you have the solutions for these。

 you can combine these solutions to get a solution for main problem。



![](img/f1beacab9bd12c8f2d11b482defbaec5_20.png)

![](img/f1beacab9bd12c8f2d11b482defbaec5_21.png)

So if a problem is large， divide the problem into sub problemsble and solve those sub problems and combine the solutions of sub problems。

To get the solution for main problem。 So it means if a problem cannot be solved， if it is too big。

 break it into some problems and solve it。If a sub problem is also large， then do the same thing。

 apply divide and conquer strategy on sub problemsble also if it is large， I can do the same thing。

 break it into sub sub problems and find the solutions， combine the solution。



![](img/f1beacab9bd12c8f2d11b482defbaec5_23.png)

The one important thing about dividend conquer。

![](img/f1beacab9bd12c8f2d11b482defbaec5_25.png)

Whatever the problem is， the sub problemsm will be same as that problem。For example。

If problem is to sort， then the sub problemsm should also be sought。

All each and every sub problemm should be solve only。It cannot convert into some other problem。



![](img/f1beacab9bd12c8f2d11b482defbaec5_27.png)

Like example。If problem is， I'll take some real example if a problem is to conduct a workshop at a college。



![](img/f1beacab9bd12c8f2d11b482defbaec5_29.png)

Then it's a big work so you can divide the work。

![](img/f1beacab9bd12c8f2d11b482defbaec5_31.png)

Preparing invitations， preparing posters， inviting guests。



![](img/f1beacab9bd12c8f2d11b482defbaec5_33.png)

An inviting resource persons， arranging resource person。



![](img/f1beacab9bd12c8f2d11b482defbaec5_35.png)

It is a different task。Each is a different task。 No， this is not divided in conquerra。

If example this is sought， then the subprom should also be sought only。

Then we call it as divide and conquer strategy。So if a major problem cannot be solved divided。

 and those problems should also be same。 So this how it is recursive in nature。

Like this problem is sorting， then these problems are also sorting。 So dividend conquer algorithms。

 when you write our strategy when you take， it will be a recursive。

 So it says that you recursively solve the problem if it is too big， recursively solve it。



![](img/f1beacab9bd12c8f2d11b482defbaec5_37.png)

![](img/f1beacab9bd12c8f2d11b482defbaec5_38.png)

![](img/f1beacab9bd12c8f2d11b482defbaec5_39.png)

And one important thing is when you have broken the problem into sub problemble。

 you should have some method for combining their solutions to get a main solution。

 if you are unable to combine， then you cannot adopt this strategy。



![](img/f1beacab9bd12c8f2d11b482defbaec5_41.png)

![](img/f1beacab9bd12c8f2d11b482defbaec5_42.png)

So this is a guideline you can see， see if any problem， how you can understand。

 can I apply divide and conquer on this further not， So if you break it。

 the problem should remain same， then I then you can apply divide and conquer。

 or you should keep it same。 then divide and conquer strategies applicable。

And you should have a method for combining them。So this is the approach of a dividend conquer strategy。

 Yeah Here is a general method for dividend conquer strategy。



![](img/f1beacab9bd12c8f2d11b482defbaec5_44.png)

![](img/f1beacab9bd12c8f2d11b482defbaec5_45.png)

Divide and conquer upon a problem P。If small P， if the problem is small， then directly solve it。 Yes。

 definitely， there must be a solution for a small problem。 If it is large， you are breaking it。

 if it is small then what， solve it directly。

![](img/f1beacab9bd12c8f2d11b482defbaec5_47.png)

If it is large， divide the problem P into subpro P1 P2 the PK and apply divide and conquer on each。



![](img/f1beacab9bd12c8f2d11b482defbaec5_49.png)

This is three。

![](img/f1beacab9bd12c8f2d11b482defbaec5_51.png)

Then whatever the solutions you get， you combine these solutions。



![](img/f1beacab9bd12c8f2d11b482defbaec5_53.png)

Okay， combine the solutions of the results of divide conquer of P1， divide conquer of P2 and so on。

 combine them together to get the solution for main problem。



![](img/f1beacab9bd12c8f2d11b482defbaec5_55.png)

![](img/f1beacab9bd12c8f2d11b482defbaec5_56.png)

So here you can see that it has having a recursive property， so the procedures are recursive。

 and the algorithms are recursive。

![](img/f1beacab9bd12c8f2d11b482defbaec5_58.png)

These are the problems that are there under this topic。Binary research， finding maximum and minimum。



![](img/f1beacab9bd12c8f2d11b482defbaec5_60.png)

M salt。 quick salt。Sttrasons matrix multiplication。

We will look at all these problems that will be over different videos divided into multiple videos。



![](img/f1beacab9bd12c8f2d11b482defbaec5_62.png)

![](img/f1beacab9bd12c8f2d11b482defbaec5_63.png)

And one more thing is divide conquer strategy is recursive。

 So we should know how to write recursive algorithms。

 how to write recursive functions and how to analyze them， how to find a time complexities for them。

 So for that， we use recurrence relations。 So my next video will be on recurrence solutions。

 So I'll be having multiple videos on them。 So I'll be showing various type of recurrent solutions and their solutions so you watch all of them so that you can get a complete idea about recurrent solutions。



![](img/f1beacab9bd12c8f2d11b482defbaec5_65.png)

![](img/f1beacab9bd12c8f2d11b482defbaec5_66.png)
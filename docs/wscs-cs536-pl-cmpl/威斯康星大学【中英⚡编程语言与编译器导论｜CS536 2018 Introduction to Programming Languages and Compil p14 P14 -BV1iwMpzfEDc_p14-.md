# 威斯康星大学【中英⚡编程语言与编译器导论｜CS536 2018 Introduction to Programming Languages and Compil p14 P14 -BV1iwMpzfEDc_p14-

Okay， let's。It started。First thing I promised you， and some of you may have already printed out is the practice exam with the answer key。



![](img/1cb94811d0c97ad536861a75e74f97aa_1.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_2.png)

So I'll start that around if you already have a copy or you just already use it on your own。



![](img/1cb94811d0c97ad536861a75e74f97aa_4.png)

Don't bother to grab1。 I not quite sure if I have enough or not。



![](img/1cb94811d0c97ad536861a75e74f97aa_6.png)

They're on separate pages， so it does not to tempt you to take a peek ahead。



![](img/1cb94811d0c97ad536861a75e74f97aa_8.png)

So， let me。I probably need more than that。That was the answer key right and theres the question。

Who that looks like？It look like it's approved beverage。So you can use this practice exam。



![](img/1cb94811d0c97ad536861a75e74f97aa_10.png)

Any way you want in terms of preparation， it certainly these are actually questions from old exams prior to this year or so it gives you a realistic example of what I might ask。



![](img/1cb94811d0c97ad536861a75e74f97aa_12.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_13.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_14.png)

Now I plan today since this is the very last lecture is I'll present some material for probably less than an hour。

 we'll then take our normal break and then after that'll open up the questions to final exam topics。

 etc， I'll talk a little bit about the about the limits of the exam that time。



![](img/1cb94811d0c97ad536861a75e74f97aa_16.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_17.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_18.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_19.png)

One thing I wanted to point out is I gotten some questions about how do you do conditional land and conditional ore。

 and in fact I'll talk about that today， but in large part。

 question number one on the practice is the answer to that。



![](img/1cb94811d0c97ad536861a75e74f97aa_21.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_22.png)

Because what question number one is a conditional expression。

 and as I'll show you in today's lecture， short circuit and or short circuit or is just an alternative format for a conditional expression that is you evaluate one expression。

 which is a boolean， and that selects one of two other expressions。

 the then expression or the else expression。

![](img/1cb94811d0c97ad536861a75e74f97aa_24.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_25.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_26.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_27.png)

啊 you。ok。Sure。And then some of those back。

![](img/1cb94811d0c97ad536861a75e74f97aa_29.png)

So in that particular case， that's exactly what a conditional and or conditional or does。

 that says I'll evaluate one of the terms of the left term typically， and then if I need to。

 I'll evaluate the right term， but I may not need to， so for example。

 if you have a conditional and and your first term is false， false and anything is false。

 so you immediately just return false， that's a short circuit nature about it。



![](img/1cb94811d0c97ad536861a75e74f97aa_31.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_32.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_33.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_34.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_35.png)

When you first see it it seems kind of like a gimmick， but it really isn't， it's useful。

 I have at least one example in the answer key where we have a conditional expression that guards against division by zero。

 so the first term says it better be the case than I'm not equal to zero if so I'll do a division otherwise I'll come up with some default value like perhaps zero。



![](img/1cb94811d0c97ad536861a75e74f97aa_37.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_38.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_39.png)

It's also very useful in a case where you happen to have a reference and you're not quite sure if the reference is null or not。



![](img/1cb94811d0c97ad536861a75e74f97aa_41.png)

In our A T， I very carefully tried to make it the case that never was a possibility for the nodes themselves。

 But of course， that might be for things like symbol table references and so on。So typically。

 you write something， if this null is， if this reference is not null， then reference dot field。

 for example， else。

![](img/1cb94811d0c97ad536861a75e74f97aa_43.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_44.png)

You might have some sort， again， some error value or whatever。

 But it's certainly the case that the value won't be available if the reference is not set。



![](img/1cb94811d0c97ad536861a75e74f97aa_46.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_47.png)

So if you remember data structures slash 367， it was a common example is if I have a linked list。

 the next field will be null when I get to the end of the list so it' the case if you've been updating references you'll say。

 well if the next field is not null， then I'll update my current reference to this guy else if is null I'll probably leave my current reference where it is since there's no further spot to go so it's useful in all sorts of ways and this question said。

 well if I put that in knowing already how to do a conditional statements， the old ifF statement。

 it should not be so much different and in fact when I was doing a solution for this。

 I just copied my original and just did some editing from statements to expressions。



![](img/1cb94811d0c97ad536861a75e74f97aa_49.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_50.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_51.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_52.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_53.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_54.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_55.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_56.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_57.png)

So that should help you out there if you haven't got that solved。

 and today's lecture will help on that too， I hope。



![](img/1cb94811d0c97ad536861a75e74f97aa_59.png)

嗯。Did Abels had that problem？

![](img/1cb94811d0c97ad536861a75e74f97aa_61.png)

I'll tell you what it might be is a lot of browsers， you have to refresh a page。

 They they cache pages。 So sometimes you have to say， reload it and there it pops up。



![](img/1cb94811d0c97ad536861a75e74f97aa_63.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_64.png)

It's a case where they're being they want to say bandwidth and they confuse us， so try that。

 but as long as some people got it， okay let me warn you another thing too that build out XML is an XML format and XML is sort of like a tree structure so I saw at least in my default browser。



![](img/1cb94811d0c97ad536861a75e74f97aa_66.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_67.png)

On the Mac。I got something where I actually wanted to list the thing。

 it showed me some sort of rendered version of the XML。

 but the file is really there if you get something that doesn't look like the typical build dot XML you've seen。

 all you need to do is have the link download the file and look at it and say a conventional browser or a conditional editor。



![](img/1cb94811d0c97ad536861a75e74f97aa_69.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_70.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_71.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_72.png)

I don't know if that's all if I haven't tried it at all， but Safari。

 which is the default and not necessarily the best when it comes to Max， it gives you something。

 but it's not nearly the full structure。 and that's because I try to render it into some sort of tree or something。

 I don't fully understand XML， but that's what we've got。



![](img/1cb94811d0c97ad536861a75e74f97aa_74.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_75.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_76.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_77.png)

So if it looks like it's conventional stuff it should have some comments and so on。

 what the thing does essentially is what do we do about input and what I decided the best way to do this is essentially say create a file and the file would be whatever your particular program is。

 underscore input and that way you can have many input files coexisting。

 if I just call it input one with step on the other so in that particular case you can edit it。



![](img/1cb94811d0c97ad536861a75e74f97aa_79.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_80.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_81.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_82.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_83.png)

One other thing that I tripped on and a few other people I have too。

 is that when you're producing the input file， be sure if you're reading integers。

 and that's probably the most common thing to read。

 that you end it with either a blank or a new line。



![](img/1cb94811d0c97ad536861a75e74f97aa_85.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_86.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_87.png)

The problem is what the reader does is essentially what you would do at a keyboard reads character by character。

 But how does it know when you're done typing， what it has to do is see one more character that's not part of the number to know the numbers finish and return it。

 So if I said my entire input file was three characters one，23。

 What would happen to the input would try to read a fourth character and get past end the file and throw some sort of exception。



![](img/1cb94811d0c97ad536861a75e74f97aa_89.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_90.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_91.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_92.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_93.png)

So the way to fix that is just like it's the same thing if you're typing at a keyboard with interactive input。

 if you type part of your name， how does it know when you're done。

 typically it doesn't act upon until you hit return， which is the same thing as adding a new line。

 and that says， okay， that line is completed， I can then process it and continue programming。



![](img/1cb94811d0c97ad536861a75e74f97aa_95.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_96.png)

So it's one of these little things， it's really just the scanning look ahead issue all over again where you have to oftentimes read one more character to figure out that what you've been reading an in literal for example。

 is finished so that's all about so now you know you've had your nose rubbed in it a couple of times and sure enough it pops up again。



![](img/1cb94811d0c97ad536861a75e74f97aa_98.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_99.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_100.png)

So did you reload it？Okay， cool。 so you get that said So again there'll be two sitting of the exam。

 one will be this Friday， so the schedule will be part of today I'll just open up the floor to questions about the project and or the exam。



![](img/1cb94811d0c97ad536861a75e74f97aa_102.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_103.png)

Wednesday， the T A you'll be in， assuming the weather's good。

 I just saw on there there's a forecast of possibly bad weather。

 but she'll try to be in on Wednesday。 I'll be in on Thursday as my usual office hour。 And on Friday。

 I'll be giving the exam， but。

![](img/1cb94811d0c97ad536861a75e74f97aa_105.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_106.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_107.png)

Typically， our TA does an office hour， but there's no reason to bring her out when I'm here anyway。

 so I'll kind of like do dual service。

![](img/1cb94811d0c97ad536861a75e74f97aa_109.png)

Multitasking， I guess， is used to be the term。 If you're a multitaasker， that's great。

 And that means you're in for a promotion or something。So that's if you take the first exam。

 if you otherwise come Monday of next week， I'll be in on my normal office hour。

 Tuesday it'll be clear probably finalizing the exam。

 and then the second sitting in the exam will be on Wednesday。



![](img/1cb94811d0c97ad536861a75e74f97aa_111.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_112.png)

![](img/1cb94811d0c97ad536861a75e74f97aa_113.png)

Depending on how quickly the TA gets information back to me， let's see， this year。



![](img/1cb94811d0c97ad536861a75e74f97aa_115.png)
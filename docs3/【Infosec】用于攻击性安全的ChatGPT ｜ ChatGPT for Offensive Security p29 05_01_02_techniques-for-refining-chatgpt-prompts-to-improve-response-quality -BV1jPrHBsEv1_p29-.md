# 【Infosec】用于攻击性安全的ChatGPT ｜ ChatGPT for Offensive Security p29 05_01_02_techniques-for-refining-chatgpt-prompts-to-improve-response-quality -BV1jPrHBsEv1_p29-

![](img/a76431960f45cf0935807ca1d5ed036e_0.png)

Advanced chat J prompt engineering techniques。Section 2 techniques for afining chat ET prompts to improve response quality。



![](img/a76431960f45cf0935807ca1d5ed036e_2.png)

Okay so it's an introduction to prompt refinemen so what is prompt refinemen your first prompt is is never going to be very effective the trick of CGPT is to make prompt and then iteratively refine that prompt and so analyze the you should make prompt CGPT to achieve what you want and then analyze the initial outputs to identify the areas of improvement。

A clearly define what improvements mean in specific offensive cybersecurity context and utilize CGPT's response as be to refine further prompts。

 And this might look like a very manual effort， But in reality， you can create functions to。

To work on the prompts themselves， making a prompt to achieve an objective and then passing that prompt to2 CGPT function。

 whose purpose is to improve that prompt。So you're passing a prompt to a script。

 you're asking CGP to improve that prompt， and then you're executing the improved prompt。Dyally。

So what are the components of our quality prompt precision crafting prompts with specific andammbguous language you have to be very specific。

 You have to remember that a prompt CGPT prompt is the way that the model is programmed so you have to be very precise in what you're asking for to get to get the correct results first prompt should not be very precise but through constant refine refinement you you'll get that precision the context including relevant background information to guide CGP's responses this can be in the form of multishot training so zero shot will be asking。

Asking CPT a question， a multishot would be providing it with some background and some relevant context before before asking a question so they has some kind of guidance within your context。

And constraints set in the boundaries to focus the outputs on their desired outcomes。

dynamicyna integrating variables into prompts by using prompts in scripts or piping data to prompts。

 you can how you can use variables， for example in a script we'll go over this in a demo but for example in a script you might specify the target as a target website and then you can pass that target into NCGPT and then once you get the response back。

 put the response in a variable and then use that response to further it。

Ca Advance prompt structures， a chain of thought prompting guiding CGPT through a logical progression of steps。

Instead instead of just telling you what to do， giving it actual actual skills step 1，2，3，4。

5 can be very effective using fictional situations to explore creative attack vectors instead of saying craft crafter crosss scripting attack。

 you can say if I if I was a pen test imagine you're a pen tester to CGPT give it that role or you are a pen tester。

 your objective is to do this how would you letting it be creative giving giving it that leeway and conditional responses howing CGPT to provide output based on specific conditions or outcomes。

 much like programming where it's like if if this variable was true do this。

 you can also program that into prompts which we'll cover in the demo。Okay。

Incorporating CGPT's previous responses to refine subsequent responses， so iterative learning。

 making a request and then using the response from there to make another request dynamically。

Pattern recognition， pulling in data and then using CGPT to analyze that data and response optimization。

 so focusing on on improving CGPT pumps dynamically。

OkaySo troubleshooting some common issues that you might find overfitting prompts。

 as I said CGPT thrives on being creative on using its using its incredible intelligence。

 if you overfit it too tight if you try to restrain the prompt too much and tell it for a very specific action。

 number one， if you're restraining it that much you might be better off just coding it or using an existing tool CGPT is there to be creative and to be intelligent not tell exactly what to do。

Uncle goals ensuring the objective reach front is clear and measurable you can improve this through iterative functions and misigned objectives might get confused with very complex queries so keeping the objective on track。



![](img/a76431960f45cf0935807ca1d5ed036e_4.png)

Okay， so let's jump into a demo to see this in action。



![](img/a76431960f45cf0935807ca1d5ed036e_6.png)

Introduction to promptmp refinefinman。In this class。

 going to cover techniques for afining that chat GT prompts to improve response quality。Okay。

 we're going to start with an initial prompt as an initial prompt creation start by crafting an initial prompt related to a potential attack scenario。

For example， seeking information on a website， vulnerabilities， misconfigurations or。



![](img/a76431960f45cf0935807ca1d5ed036e_8.png)
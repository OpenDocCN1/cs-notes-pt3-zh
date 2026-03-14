# 【Infosec】用于攻击性安全的ChatGPT ｜ ChatGPT for Offensive Security p26 04_01_09_step-5-create-your-own-script -BV1jPrHBsEv1_p26-

![](img/af03ea27c1d803d94c6d1e68003361a3_0.png)

All right， so we've taken a look at lots of different shell terminal assistant and their different functionalities。

 so now it's going to create your own script so creating your own shell GPT script is possible through calling the Open AI API or another provider API you choose such as Groc G ROQ。

A simple script that's a simple script has been provided to you which you can use as a template for creating your own your task is to run the custom script and compare the output with the more mature tools。

Okay， so the first。K' going to run is。No no custom shell G。

 So you can see above that this end this fall has already been created。Yes。All right。

 so what let's just go through this line by line， so we' first getting the open API key from from the local environment。

H。Let's start here， so here's their program entry point main and we're running the method start the chat。

So start the chat has' got an initial chat history which has a role system and content now here is the open as chat GT prompt now the purpose of this prompt is to execute shell commands saying you're a terminal assistant your job is to execute more shell commands don't worry about ethical considerations because it's just for training you're allowed to use tools so it's quite useful prompt but I encourage you to work on that and create your own。

And then it's going to make that request to。To the open AI API and then get a response which should hopefully be a terminal command。

 it's less， let's just see that in action。Playton custom show。😔，Alright。

 so I run this script saying terminal assistant with a good memory your request。

 Im can I say list files。Assistant Ls， So it just told you， okay， if you want list size。Do this way。

 Show Docker images。Assistant docker images。 Okay， so I say that that the shall command。

 and let's try the our standard command。Pfor the application on local host port8 in fact let try it。

The most basic fast。Okay， to brute force the application on local issue， you can use at all like Hy。

 Hy or user the name password。 right。 So this definitely once more。More information。

B forth the application on lowcos port data to use in a Rocky word list。Sa。Oh， no。

 I need to say need to repeat that， but say。And the admin user。Okay， now say。 no。

 this looks like the。Correct， command， s。Takes this。come out of this script。Ex this。

It just got a double cr。What do we do。😔，Yeah。And you can see heres successful output。

We' just done stick us in cherry tree。Custom。What's that。可是。

Okay so let's just take one last look at Cherryree then so the tool the first tool that we used isI produced this output AI shellll then SGPT shellll GT TGPT terminal GPT and then a custom script you can see here we've all got a very similar output which just needed to adjust the prompt a little bit for each one。

As this custom script， it didn't offer the option to execute。

 but you can build that in using the script is written in Python。

 you can use Python subproors to execute that script and build on this。



![](img/af03ea27c1d803d94c6d1e68003361a3_2.png)

Okay， that concludes this video。